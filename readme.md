# FPGA Fabric Design & Architecture
## End-to-end FPGA CAD flow and fabric architecture exploration using Verilog, Vivado, VTR, VPR, OpenFPGA, SOFA, and RISC-V.

This repository documents my hands-on work completed during the **FPGA Fabric Design & Architecture Workshop**, covering FPGA fundamentals, RTL design, Vivado implementation, timing and power analysis, open-source FPGA CAD flows, placement and routing, FPGA architecture exploration, SOFA/OpenFPGA, and RISC-V processor implementation.

The project explores the FPGA design flow from Verilog RTL to synthesis, technology mapping, placement, routing, timing analysis, resource utilization, power analysis, FPGA fabric generation, and post-implementation verification.

---

## Repository Navigation

**[Day 1 - FPGA Fundamentals & Vivado](./Day1.md)**  
  FPGA architecture, FPGA vs ASIC, LUTs, flip-flops, CLBs, Verilog counter design, Vivado simulation, synthesis, implementation, timing, power, resource utilization and VIO.

**[Day 2 - VTR & VPR FPGA CAD Flow](./Day2.md)**  
  VTR/VPR flow, architecture files, EArch FPGA architecture, technology mapping, BLIF generation, packing, placement, routing, timing constraints and FPGA reports.

**[Day 3 - RISC-V / RVMYTH on FPGA](./Day3.md)**  
  RISC-V/RVMYTH processor implementation, simulation, Vivado synthesis and implementation, FPGA resource analysis and ILA-based debugging.

**[Day 4 - Introduction to SOFA FPGA Fabric](./Day4.md)**
SOFA FPGA architecture, SkyWater 130nm technology, OpenFPGA flow, counter implementation, area, timing, power and post-implementation analysis.

**[Day 5 -  RISC-V Core on Custom SOFA Fabric](./Day5.md)**
RVMYTH RISC-V processor mapping onto the SOFA FPGA fabric, resource utilization, timing constraints, setup and hold analysis, and post-implementation verification.


---

##  Tools & Technologies

| Tool / Technology | Application |
|---|---|
| **Verilog HDL** | RTL design and simulation |
| **Xilinx Vivado** | Simulation, synthesis, implementation and FPGA analysis |
| **VTR** | FPGA CAD flow |
| **VPR** | Packing, placement and routing |
| **OpenFPGA** | FPGA fabric generation |
| **SOFA** | Custom FPGA fabric architecture |
| **RISC-V / RVMYTH** | Processor implementation |
| **SDC** | Timing constraints and timing analysis |
| **Git / GitHub** | Version control and documentation |

---

##  Technical Areas Explored

### FPGA Architecture

- FPGA vs ASIC
- LUT architecture
- Flip-flops
- Logic Elements
- Configurable Logic Blocks
- Programmable interconnect
- Switch blocks
- Connection blocks
- Clock networks
- FPGA fabric architecture

### RTL & Vivado

- Verilog RTL design
- Testbench development
- Functional simulation
- RTL elaboration
- Synthesis
- Implementation
- Timing analysis
- Power analysis
- Resource utilization
- VIO
- FPGA debugging

### FPGA CAD Flow

- VTR
- VPR
- Technology mapping
- BLIF
- Packing
- Placement
- Routing
- Architecture XML
- Netlist generation
- Timing analysis

### Timing / Area / Power

- Setup timing
- Hold timing
- Critical path analysis
- Slack
- Timing constraints
- Resource utilization
- Area analysis
- Power estimation
- Timing closure

### FPGA Fabric

- EArch architecture
- SOFA FPGA fabric
- FPGA logic architecture
- Routing architecture
- Switch blocks
- Connection blocks
- OpenFPGA
- FPGA fabric generation
- Architecture mapping

### RISC-V

- RISC-V processor architecture
- RVMYTH / Mythcore
- RTL implementation
- FPGA implementation
- ILA debugging
- Timing analysis
- Resource utilization
- Processor implementation on FPGA fabric

---

##  Technical Debugging & Problem Solving

During the practical sessions, I encountered and analyzed several issues related to FPGA design and open-source CAD flows, including:

- RTL simulation and compilation issues
- Vivado synthesis and implementation issues
- Timing constraint problems
- VTR/VPR flow issues
- Placement and routing challenges
- Netlist and simulation issues

These challenges helped me understand the practical aspects of debugging FPGA CAD flows and interpreting tool-generated reports.


---

##  Analysis & Results

The project includes analysis of:

- RTL simulation waveforms
- Synthesis results
- FPGA resource utilization
- LUT and Flip-Flop usage
- Timing reports
- Setup and hold analysis
- Critical paths
- Slack
- Power estimation
- Placement results
- Routing results
- FPGA architecture reports
- Netlist generation
- Post-synthesis simulation
- Post-implementation simulation
- FPGA fabric generation results

---

##  Project Outcomes

This project provided practical exposure to the complete FPGA implementation ecosystem:

**RTL → Simulation → Synthesis → Technology Mapping → Packing → Placement → Routing → Timing/Power/Area Analysis → FPGA Fabric → RISC-V Implementation**

The work helped build practical understanding of how **digital RTL, FPGA architecture, CAD algorithms, timing, routing and processor hardware implementation** are connected.

---

##  References

### VLSI System Design
https://www.vlsisystemdesign.com/fpga/

### RISC-V Based Microprocessor
https://github.com/shivanishah269/risc-v-core

### SOFA FPGA Framework
https://github.com/lnis-uofu/SOFA

### OpenFPGA Documentation
https://openfpga.readthedocs.io/en/master/

### VPR Documentation
https://docs.verilogtorouting.org/en/latest/vpr/

### VTR Documentation
https://docs.verilogtorouting.org/en/latest/

---

## Acknowledgement

I would like to express my sincere gratitude to **Kunal Ghosh – VSD Corp Pvt. Ltd.** and the **VSD Workshop Team** for providing the guidance, technical resources and practical learning environment for the FPGA Fabric Design & Architecture workshop.

This repository documents my hands-on learning, implementation work, simulations, screenshots, diagrams, analysis reports and observations from the practical sessions.

---
