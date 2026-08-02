# Day 4 - Introduction to SOFA FPGA Fabric

## Introduction

This focused on understanding the **SOFA (SkyWater Open-source FPGAs)** fabric and exploring FPGA implementation using the open-source **SkyWater 130nm PDK** and **OpenFPGA** framework.

SOFA provides an open-source FPGA fabric that enables the study of FPGA architecture, physical implementation, timing, area, and power using an open-source semiconductor technology.

The SOFA FPGA fabric used during the experiment was:

**FPGA1212_QLSOFA_HD_PNR**

The architecture includes:

- 1152 LUTs
- 2304 Flip-Flops
- 1152 Soft Adders
- 50 MHz maximum operating frequency

---

## SOFA FPGA Fabric

The SOFA FPGA fabric was explored to understand how a digital design is mapped onto a customized FPGA architecture.

The experiment involved analyzing:

- FPGA fabric architecture
- Logic resources
- Routing resources
- Area utilization
- Timing characteristics
- Post-implementation behavior
- Power consumption

---

## Counter Implementation on SOFA

A counter design was implemented on the SOFA FPGA fabric using the OpenFPGA flow.

The implementation results were analyzed in terms of:

- Resource utilization
- Area
- Timing
- Power
- Post-implementation simulation

---

## SOFA Counter Area

The area and resource utilization of the counter design were analyzed after mapping onto the SOFA FPGA fabric.

### Area Report

<img width="595" height="224" alt="Screenshot 2026-08-02 144833" src="https://github.com/user-attachments/assets/16c8a7b3-5232-4ec7-902a-4da731902c79" />


---

## SOFA Counter Timing

Timing analysis was performed to evaluate the performance of the counter design on the SOFA fabric.

The analysis included:

- Setup timing
- Hold timing
- Critical paths
- Timing slack
- Maximum operating frequency

### Timing Report

<img width="1279" height="886" alt="d4_sofa_timing_setup" src="https://github.com/user-attachments/assets/8b45db54-f3dd-4d86-8646-fc01af2c143d" />

<img width="557" height="350" alt="Screenshot 2026-08-02 145443" src="https://github.com/user-attachments/assets/f95ff907-d878-4576-a384-8211339a002c" />


---

## SOFA Counter Post-Implementation Simulation

Post-implementation simulation was performed to verify the functionality of the counter after mapping and implementation on the SOFA FPGA fabric.

The simulation helped verify:

- Functional correctness
- Propagation delays
- Post-implementation behavior

### Simulation Output

<img width="539" height="180" alt="Screenshot 2026-07-30 184006" src="https://github.com/user-attachments/assets/8baf6012-28aa-4075-82bd-d41cc87c3758" />


---

## SOFA Counter Power Analysis

Power analysis was performed to estimate the power consumption of the implemented counter on the SOFA FPGA fabric.

The analysis included:

- Dynamic power
- Static power
- Logic power
- Routing power
- Clock power

### Power Report

<img width="846" height="260" alt="d4_sofa_power" src="https://github.com/user-attachments/assets/0e19be21-0bc8-49ca-81cb-0e6b98530394" />


---

## Key Learning

- Explored an open-source **SOFA FPGA fabric** based on the SkyWater 130nm technology.
- Understood how a design is mapped onto a customized FPGA architecture.
- Analyzed **area, timing, power, and post-implementation behavior**.
- Gained practical exposure to **OpenFPGA-based FPGA fabric implementation**.
- Understood the relationship between FPGA architecture and implementation results.

---

## Conclusion

Day 4 provided hands-on experience with an **open-source FPGA fabric** and demonstrated how a simple RTL design can be implemented and analyzed using the **OpenFPGA and SOFA framework**.

The experiment connected FPGA architecture exploration with practical **area, timing, power, and post-implementation analysis**.
