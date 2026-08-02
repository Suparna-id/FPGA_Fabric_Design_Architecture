# Day 2 - Exploring OpenFPGA, VPR and VTR

## Introduction To OpenFPGA

The OpenFPGA framework is the first open-source FPGA IP generator which supports highly-customizable homogeneous FPGA architectures. OpenFPGA provides a full set of EDA support for customized FPGAs, including Verilog-to-bitstream generation and self-testing verification. OpenFPGA targets to democratizing FPGA technology and EDA techniques, with agile prototyping approaches and constantly evolving EDA tools for chip designers and researchers.

Some key features of OpenFPGA are:

- Use of Automation Techniques
- Reduction of FPGA development cycle to few days
- Provides open source design tools

### OpenFPGA

<img width="494" height="348" alt="Screenshot 2026-08-02 093126" src="https://github.com/user-attachments/assets/ab6075ef-9e94-4005-ba75-c97a2dd9c509" />


---

## Introduce to VPR

VPR (Versatile Place and Route) is an open source academic CAD tool designed for the exploration of new FPGA architectures and CAD algorithms, at the packing, placement and routing phases of the CAD flow. As input, VPR takes a description of an FPGA architecture along with a technology-mapped user circuit. It then performs packing, placement, and routing to map the circuit onto the FPGA. The output of VPR includes the FPGA configuration needed to implement the circuit and statistics about the final mapped design (eg. critical path delay, area, etc).

### VPR GUI Visualisation

<img width="614" height="419" alt="Screenshot 2026-07-29 103436" src="https://github.com/user-attachments/assets/7b37b6d7-8680-4e76-8b2b-77735d41b6a0" /> 


**Nets**

<img width="954" height="415" alt="Screenshot 2026-07-29 105027" src="https://github.com/user-attachments/assets/19eacdf7-e0ae-402b-9b80-597ae73dae53" />


**Critical Path**

<img width="511" height="389" alt="Screenshot 2026-07-29 103940" src="https://github.com/user-attachments/assets/ea3e59c9-d9f3-4f0b-a034-5f350987d645" />


**VPR utilization**

<img width="705" height="416" alt="Screenshot 2026-07-29 142932" src="https://github.com/user-attachments/assets/64490a38-891e-4cdc-b256-bf59007a93c8" />

---

**To invoke VPR from terminal:**

```
$VTR_ROOT/vpr/vpr \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
<blif-file-path> \
--route_chan_width 100 \
--disp on
```

**The VPR flow was executed using the following command:**
```
$VTR_ROOT/vpr/vpr \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
$VTR_ROOT/vtr_flow/benchmarks/blif/tseng.blif \
--route_chan_width 100 \
--disp on
```
---

## Timing Analysis using Constraints

Timing constraints were added using an SDC file.In order to perform timing analysis,a constraint file needs to be created. This constraint file is provided as an input to tool.To perform timing analysis from command-line, below mentioned switch should be enabled.
The constraints file defines:

## SDC Constraint File

**Constraint File**

```
create_clock -period 10 -name pclk
set_input_delay -clock pclk -max 0 [get_ports {*}]
set_output_delay -clock pclk -max 0 [get_ports {*}]
```
**Running VPR with Constraints**

```
$VTR_ROOT/vpr/vpr \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
$VTR_ROOT/vtr_flow/benchmarks/blif/tseng.blif \
--route_chan_width 100 \
--sdc_file tseng.sdc \
--disp on
```
---

## Setup and hold Timing Analysis using VPR timing analysis

Setup timing checks whether data reaches destination registers before the active clock edge.

### Setup Timing Report
<img width="525" height="368" alt="Screenshot 2026-07-29 173349" src="https://github.com/user-attachments/assets/b9e3d8bd-e0a1-4979-9ccb-2ae09e860af4" />

### Hold Timing Report
<img width="495" height="178" alt="Screenshot 2026-08-02 101941" src="https://github.com/user-attachments/assets/d9fe4a5b-598b-4d82-afbb-3fa8db879b25" />

---

## Introduction to VTR

VTR (Verilog-To-Routing) is a complete open-source FPGA CAD flow.

<img width="457" height="367" alt="Screenshot 2026-08-02 102839" src="https://github.com/user-attachments/assets/223c4eaa-3986-4138-ac94-7bd714e251d8" />

### VTR Flow Command

```
$VTR_ROOT/vtr_flow/scripts/run_vtr_flow.py \
counter.v \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
-temp_dir . \
-route_chan_width 100
Counter Design for VTR Flow
```
The following counter design was used for VTR implementation.

**Counter Verilog Code**
```
module up_counter (
out      ,
enable   ,
clk      ,
reset
);

output reg [3:0] out;

input enable, clk, reset;

reg [3:0] out;

always @(posedge clk) begin

if (reset)
    out <= 4'b0000 ;
else if (enable)
    out <= out + 1'b1;
end
endmodule
```
---

**The generated reports included:**

<img width="486" height="413" alt="Screenshot 2026-07-30 164528" src="https://github.com/user-attachments/assets/92d446b4-bd8b-4ecd-bef0-f1bf1edc2d24" />

<img width="394" height="386" alt="Screenshot 2026-07-30 171355" src="https://github.com/user-attachments/assets/ed1240dd-e2f3-4260-a6aa-58417999be89" />

---

## SDC Constraint File
**Constraint File**
```
create_clock -period 10 up_counter_clk
set_input_delay -clock up_counter_clk -max 0 [get_ports {*}]
set_output_delay -clock up_counter_clk -max 0 [get_ports {*}]
```

**Running VPR with Constraints**
```
$VTR_ROOT/vpr/vpr \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
counter.pre-vpr.blif \
--route_chan_width 100 \
--sdc_file counter.sdc
```

## Setup Timing Report

After adding timing constraints:

<img width="491" height="340" alt="Screenshot 2026-08-02 110331" src="https://github.com/user-attachments/assets/3a91eb8b-fa69-45c9-a8a8-88aec83332ed" />

## Hold Timing Report 

<img width="384" height="268" alt="Screenshot 2026-07-31 160716" src="https://github.com/user-attachments/assets/7f13e81b-633b-4148-a2ae-9b89acee1ff6" />

---
**Post Synthesis Simulation**

Post synthesis simulation was performed using:
```
Generated post synthesis netlist
SDF timing file
Vivado simulator
```

**The generated files:**

up_counter_post_synthesis.v
up_counter_post_synthesis.sdf

**Generating Post Synthesis Netlist**
```
$VTR_ROOT/vpr/vpr \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
counter.pre-vpr.blif \
--gen_post_synthesis_netlist on
```
---
## Testbench for Post Synthesis Simulation

**Counter Testbench**
```
`timescale 1ns/1ps

module up_counter_tb();

reg clk, reset, enable;
wire [3:0] out;

up_counter dut(
    .\up_counter^enable (enable),
    .\up_counter^clk (clk),
    .\up_counter^reset (reset),
    .\up_counter^out~0 (out[0]),
    .\up_counter^out~1 (out[1]),
    .\up_counter^out~2 (out[2]),
    .\up_counter^out~3 (out[3])
);

initial $sdf_annotate("up_counter_post_synthesis.sdf", dut);

initial begin

clk=0;
enable=0;
reset=1;

#20;

reset=0;
enable=1;

end

always
#5 clk=~clk;

endmodule
```
---
## Post Synthesis Simulation Results

**The generated post synthesis simulation verified:**

>> Timing behavior
>> Routing delays
>> Gate-level functionality

**Post Synthesis Waveform**

<img width="539" height="180" alt="Screenshot 2026-07-30 184006" src="https://github.com/user-attachments/assets/cbedad99-17c5-435b-858b-011211146725" />


---

## Power Analysis using VTR

Power estimation was performed using VTR power analysis flow.

**Power Analysis Command**
```
$VTR_ROOT/vtr_flow/scripts/run_vtr_flow.py \
counter.v \
$VTR_ROOT/vtr_flow/arch/timing/EArch.xml \
-power \
-temp_dir . \
-route_chan_width 100
```
---

## stdout.log report

<img width="535" height="337" alt="Screenshot 2026-08-02 111706" src="https://github.com/user-attachments/assets/c42bad77-5076-4fc9-a944-de4c7f38dfe2" />

---

## Power Report

**Power Analysis report using VTR**

<img width="550" height="403" alt="Screenshot 2026-08-02 112251" src="https://github.com/user-attachments/assets/011bfba2-ee86-4f19-a8c8-d3836e4f6b59" />

---
