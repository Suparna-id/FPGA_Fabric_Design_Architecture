# Day 1 - Exploring FPGA Basics and Vivado

## FPGA Architecture

FPGA (Field Programmable Gate Array) is a reconfigurable digital device that can be programmed to implement different hardware functionalities.

The FPGA architecture primarily consists of:

- Configurable Logic Blocks (CLBs)
- Programmable Interconnects
- Input/Output (I/O) Blocks
- Memory / Block RAM
- DSP Resources
- Clocking Resources

<img width="1920" height="1312" alt="FPGA-Graphics-1" src="https://github.com/user-attachments/assets/b377cd42-09e4-44f3-a0f9-79b87d9ef04e" />



---

## Configurable Logic Block

A Configurable Logic Block (CLB) is one of the fundamental building blocks of an FPGA and is responsible for implementing combinational and sequential logic.

A CLB generally consists of:

- Look-Up Tables (LUTs) - Logic function implementation
- Carry and Control Logic - Arithmetic operations
- Flip-Flops - Sequential logic storage
- Multiplexers and routing resources

<img width="355" height="324" alt="CLB" src="https://github.com/user-attachments/assets/35661afd-a6cf-4a3e-b96e-08fad3445902" />


---

## Basys 3 FPGA Board

The FPGA board used in this workshop is the **Basys 3 Artix-7 FPGA Board**.

The Basys 3 board provides various peripherals and interfaces for FPGA development, including LEDs, switches, push buttons, seven-segment display, USB/JTAG interface, VGA and clock resources.

<img width="771" height="742" alt="basys3_rm" src="https://github.com/user-attachments/assets/30beff3a-ae8e-455f-aa63-c28bb36ff799" />

---

## Counter Example in Vivado

A **4-bit up-counter with clock division** was implemented using Verilog HDL to explore the Vivado FPGA design flow.

The design consists of two main sections:

1. Clock division
2. 4-bit counter

The input clock is divided to generate a slower clock, and the 4-bit counter increments on every positive edge of the divided clock.

### Verilog RTL

```verilog
`timescale 1ns / 1ps

module counter_clk_div(
    input clk,
    input rst,
    output reg [3:0] counter_out
);

reg div_clk;
reg [25:0] delay_count;

// Clock division block
always @(posedge clk) begin
    if(rst) begin
        delay_count <= 26'd0;
        div_clk <= 1'b0;
    end
    else begin
        if(delay_count == 26'd212) begin
            delay_count <= 26'd0;
            div_clk <= ~div_clk;
        end
        else begin
            delay_count <= delay_count + 1;
        end
    end
end

// 4-bit counter block
always @(posedge div_clk) begin
    if(rst)
        counter_out <= 4'b0000;
    else
        counter_out <= counter_out + 1;
end

endmodule


---

## Behavioral Simulation

Behavioral simulation was performed using the Vivado simulator to verify the functionality of the counter before synthesis.
The snippet below shows the behavioural simulation for the 4-bit up counter.

### Simulation Output

<img width="551" height="268" alt="Screenshot 2026-07-27 150505" src="https://github.com/user-attachments/assets/716d1508-d4b9-49c6-a8b5-8ad12ab4fa19" />


---

## RTL Elaboration

RTL elaboration converts the Verilog HDL design into an RTL schematic representation.
The snippet below is the schematic of the counter design after elaboration.


This stage verifies:

- Logical connectivity
- Module hierarchy
- Register structure
- Signal flow

### RTL Schematic

<img width="710" height="235" alt="Screenshot 2026-07-27 152240" src="https://github.com/user-attachments/assets/f015cf26-1865-4c9c-b521-637799de738c" />

---

## Constraints and Pin Mapping

Constraints were added using the `.xdc` file.

The constraints file maps:

- Clock input pin
- Reset input pin
- Output LED pins
- I/O standards

### Constraint.xdc

<img width="722" height="302" alt="Screenshot 2026-07-27 152217" src="https://github.com/user-attachments/assets/05d39907-56b9-47a8-b838-0b3310f38b59" />


### Package Mapping

<img width="725" height="332" alt="Screenshot 2026-07-27 151211" src="https://github.com/user-attachments/assets/ea6aecc5-af0c-4a27-88cb-6f223cb23a10" />


*FPGA package view showing the physical pin assignments.*

---

## Synthesis

Synthesis converts the RTL design into a technology-specific FPGA netlist using available FPGA resources such as:

- LUTs
- Flip-Flops
- Carry Chains
- Multiplexers

During synthesis:

- Logic optimization is performed
- Resource utilization is estimated
- Timing information is generated
- The RTL is mapped to FPGA-specific resources

### Synthesized Design

<img width="774" height="344" alt="Screenshot 2026-07-28 121231" src="https://github.com/user-attachments/assets/6b6df5db-5b0c-4cd2-b93b-7dc0c47c6b9c" />


---

## Timing Analysis

Timing analysis verifies whether signals reach their destination registers within the required timing constraints.

Two important timing checks are:

- Setup Timing
- Hold Timing

### Setup Timing

Setup timing ensures that data reaches the destination register before the active clock edge.

A simplified setup timing relationship is:

\[
T_{cq} + T_{logic} + T_{setup} < T_{clock}
\]

### Hold Timing

Hold timing ensures that data remains stable for the required period after the active clock edge.

### Slack

Slack is defined as:

\[Slack = Required\ Time - Arrival\ Time\]

Positive slack indicates that the timing requirement is satisfied.

### Design Timing Summary

<img width="941" height="233" alt="Screenshot 2026-07-28 122324" src="https://github.com/user-attachments/assets/30638443-aced-482d-9775-ebc09c35e644" />


*Timing analysis summary of the implemented counter design.*

---

## Device Utilization

Vivado generates utilization reports showing the FPGA resources consumed by the implemented design.

Resources analyzed include:

- LUTs
- Flip-Flops
- I/O pins
- Other FPGA resources reported by Vivado

### Utilization Report

<img width="754" height="359" alt="Screenshot 2026-07-28 122555" src="https://github.com/user-attachments/assets/dad4b46d-eee9-4d1e-ae78-9d45c3f8e2e9" />

*FPGA resource utilization report after implementation.*

---

## Power Analysis

Power analysis estimates the power consumption of the implemented FPGA design.

The analysis includes:

- Dynamic power
- Static power
- Clock power
- Signal power
- I/O power

### Power Report

<img width="767" height="391" alt="Screenshot 2026-07-28 122433" src="https://github.com/user-attachments/assets/290571d9-9567-441d-a891-2d7503ff0747" />


*Power analysis report generated after FPGA implementation.*

---

## Virtual Input/Output (VIO)

Virtual Input/Output (VIO) is a customizable Vivado IP core that allows internal FPGA signals to be monitored and controlled in real time using the Vivado Hardware Manager.

Applications include:

- Internal debugging
- Signal monitoring
- Runtime testing
- Hardware verification

### VIO Implementation

Virtual Input/Output (VIO) core is a customizable core that can both monitor and drive internal FPGA signals in real time. The number and width of the input and output ports are customizable in size to interface with the FPGA design.
