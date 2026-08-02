# Day 3 - Mythcore Processor Implementation and FPGA Analysis
---
## Objective

The objective of Day 3 was to work with a more complex RTL design instead of a simple counter circuit.

A 4-stage pipelined RISC-V core, named RVMYTH, is used in the repository. A complete RTL to Bitstream flow is implemented over the RVMYTH core. The Core is initially developed in High-level language named TL-Verilog and finally compiled to Verilog HDL.A Mythcore RISC-V based processor design was taken and implemented on FPGA.

The work involved:

<img width="1536" height="1024" alt="ChatGPT Image Aug 2, 2026, 12_43_15 PM" src="https://github.com/user-attachments/assets/e0e07421-fbfc-4c06-8e07-b2751647f612" />


This experiment helped in understanding how larger digital systems behave on FPGA architectures and how FPGA tools analyze timing, routing, area, and power.

---

# Mythcore Design Source

The following files were used for the Mythcore processor implementation:

```text
mythcore_test.v
mythcore_test_gn.v

----
# RTL to Synthesis

## RTL Simulation Output

<img width="677" height="163" alt="Screenshot 2026-07-31 181942" src="https://github.com/user-attachments/assets/6cb6b662-92a1-48d3-8aed-5c2a1371ff33" />

---

## RTL Schematic Output 

<img width="1273" height="877" alt="d3_rvmyth_synth_sch" src="https://github.com/user-attachments/assets/9dfc4aa9-ae32-4f77-ba0f-afbb5e969966" />

---

## Package View

The package view displayed FPGA resource placement and I/O pin allocation.

This helped in understanding:

>> Physical FPGA layout
>> Resource mapping
>> Pin assignments
>> FPGA routing regions


## Package View Output

<img width="332" height="230" alt="Screenshot 2026-07-31 182621" src="https://github.com/user-attachments/assets/cf1e3e77-9337-43eb-9f77-44bde1f22686" />

----

## Integrated Logic Analyzer (ILA)

**Objective**

ILA was added to debug and monitor internal FPGA signals in real time.

Instead of only viewing external outputs, ILA allows internal processor signals to be captured directly using Vivado Hardware Manager.

---

ILA Instantiation

```
ila_0 your_instance_name (
    .clk(clk),

    .probe0(reset),
    .probe1(out)
);
```
---

## ILA Connections

The following signals were connected:

| Signal | Purpose |
|---|---|
| `clk` | Clock input |
| `reset` | Reset signal |
| `out` | Output probe |

---
## Constraint File

<img width="358" height="183" alt="Screenshot 2026-07-31 182140" src="https://github.com/user-attachments/assets/d168302c-dd79-4a4f-9904-bc48c519d08c" />

---

## Utilization Analysis

<img width="609" height="146" alt="Screenshot 2026-07-31 182807" src="https://github.com/user-attachments/assets/6dd26534-34a8-4c48-af62-a845f591e98c" />

---

## Timing Analysis

<img width="596" height="133" alt="Screenshot 2026-07-31 182749" src="https://github.com/user-attachments/assets/df051a4e-2f18-471a-a5b5-92ff57eb2a00" />

---

## Power Analysis

<img width="589" height="207" alt="Screenshot 2026-07-31 182831" src="https://github.com/user-attachments/assets/713d8548-d0cc-45b9-ab23-eccc679307c1" />

---

## Conclusion

- Implemented and analyzed the Mythcore RISC-V processor using Vivado.
- Verified the design through RTL simulation and synthesis.
- Studied FPGA resource utilization, timing, and power reports.
- Examined the synthesized schematic and package mapping.
- Integrated **ILA** for real-time monitoring and hardware debugging.
- Gained practical understanding of implementing and debugging a **processor-based RTL design on FPGA**.

---
