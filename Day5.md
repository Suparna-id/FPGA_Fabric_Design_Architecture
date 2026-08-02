# Day 5 - RISC-V Core on Custom SOFA FPGA Fabric

## Introduction

Day 5 focused on implementing the **RVMYTH RISC-V processor core** on the custom **SOFA FPGA fabric** using the **OpenFPGA and VTR framework**.

The experiment extended the previous SOFA counter implementation to a significantly larger processor-based design and involved:

- RISC-V processor mapping
- FPGA resource utilization analysis
- Timing constraint definition
- Placement and routing
- Setup and hold timing analysis
- Post-implementation simulation
- FPGA architecture analysis

---

## RVMYTH Implementation on SOFA

The RVMYTH RISC-V core was mapped onto the custom SOFA FPGA architecture through the OpenFPGA/VTR flow.

The implementation generated detailed reports related to:

- Logic utilization
- Netlist statistics
- Routing resources
- Timing
- FPGA primitive usage
- Post-implementation simulation

### RVMYTH Utilization Report

The utilization report provides information about the FPGA resources required by the RVMYTH processor after synthesis and mapping.

### Circuit Statistics

- Total Blocks: 5526
- Inputs: 2
- Latches: 1807
- Outputs: 8
- 0-LUTs: 4
- 4-LUTs: 3705

### Net Statistics

- Total Nets: 5518
- Average Fanout: 3.1
- Maximum Fanout: 1807
- Minimum Fanout: 1.0

### Timing Graph

- Timing Graph Nodes: 22705
- Netlist Clocks: 1

---

### Utilization Report

<img width="1100" height="329" alt="d5_area" src="https://github.com/user-attachments/assets/8c2447dc-317e-42e4-b724-0a8d382e15b9" />

<img width="668" height="108" alt="d5_logic_elements" src="https://github.com/user-attachments/assets/4a4a806e-719d-4a1e-87c2-df1b61ce29d8" />

---

## Timing Constraints

An SDC constraint file was created to define the clock and I/O timing requirements for the RVMYTH implementation.

### SDC Constraint File

```tcl
create_clock -period 200 clk
set_input_delay -clock clk -max 0 [get_ports {*}]
set_output_delay -clock clk -max 0 [get_ports {*}]
```

---

## Setup Timing Analysis

Setup timing analysis was performed after placement and routing to verify whether data reaches the destination within the required clock period.

<img width="1275" height="883" alt="d5_timing_setup" src="https://github.com/user-attachments/assets/6e76b9f0-234c-4cbe-a3ee-5933568df441" />


---

## Hold Timing Analysis

Hold timing analysis was performed to verify that data remains stable for the required time after the active clock edge.

<img width="1276" height="883" alt="d5_timing_hold" src="https://github.com/user-attachments/assets/b7779902-3a40-42c7-ab34-916b5fe36bef" />


---

## Post-Implementation Simulation

Post-implementation simulation was performed on the generated RVMYTH implementation to verify the behavior of the processor after synthesis, placement, and routing.

<img width="1277" height="882" alt="d5_post_impl_sim" src="https://github.com/user-attachments/assets/7157eed8-01c5-4fc5-8458-af6bb91891b9" />


---

## Key Observations
- The RVMYTH RISC-V processor was successfully mapped onto the custom SOFA FPGA fabric.
- The processor required significantly more FPGA resources than the smaller counter design.
- The implementation generated detailed netlist, utilization, routing, and timing information.
- Setup and hold timing were analyzed using the defined SDC constraints.
- Post-implementation simulation was used to verify the implemented processor behavior.
- The experiment demonstrated the scalability of the SOFA/OpenFPGA flow from a simple RTL design to a processor-based architecture.

---

## Conclusion

- Mapped the RVMYTH RISC-V processor onto the custom SOFA FPGA fabric.
- Explored resource utilization, netlist statistics, routing, and timing reports.
- Applied SDC timing constraints and analyzed setup and hold timing.
- Performed post-implementation simulation to observe the behavior of the implemented processor.
- Gained practical experience with the OpenFPGA + VTR flow for custom FPGA architecture exploration.
- Completed the workshop progression from basic RTL design to processor implementation on an open-source FPGA fabric.

---
