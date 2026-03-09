# RAM Model using Verilog HDL

## Overview
This project implements a **parameterized RAM (Random Access Memory) model** using **Verilog HDL**. The RAM supports basic **read and write operations** using control signals and address inputs.  

The project demonstrates the complete digital design flow including **Verilog implementation, simulation, synthesis with constraints, and generation of area, timing, and power reports**.

---

## Features
- Parameterized RAM design
- Configurable address size
- Configurable word size
- Read and write operations
- High impedance data bus when inactive
- Verilog HDL implementation
- Synthesis using timing constraints
- Area, timing, and power report generation

---

## RAM Architecture

The RAM consists of the following components:

- **Address Bus** – selects a specific memory location  
- **Data Bus** – bidirectional data transfer  
- **Control Signals**
  - `CS` – Chip Select  
  - `WE` – Write Enable  
  - `OE` – Output Enable  

Memory is implemented using a **register array**.

Memory size:

Memory Locations = 2^(AddressSize)  
Word Size = WordSize bits

---

## Project Files

project/

ram_model.v → Verilog RAM design  
ram_model_test.v → Testbench for simulation  
ram_model.sdc → Synthesis timing constraints  

ram_model_netlist.v → Synthesized gate-level netlist  

ram_model_area.rpt → Area report  
ram_model_timing.rpt → Timing report  
ram_model_power.rpt → Power report  

---

## Module Description

### Top Module
RamChip

### Parameters
AddressSize – Number of address bits  
WordSize – Size of each memory word  

### Inputs
Address → Address input  
CS → Chip select  
WE → Write enable  
OE → Output enable  

### Inout
Data → Bidirectional data bus

---

## Operation

### Write Operation
Data is written to memory when:

CS = 0  
WE = 0  

The value on the **Data bus** is stored in the memory location specified by the address.

---

### Read Operation
Data is read from memory when:

CS = 0  
OE = 0  

The memory contents at the selected address are placed on the **Data bus**.

---

### High Impedance State
If the RAM is not selected or output is disabled, the data bus remains in:

Z (High Impedance)

---

## Simulation
The design is verified using the **testbench (ram_model_test.v)**.  
Simulation checks correct behavior of:

- Memory write operations
- Memory read operations
- Control signal behavior
- High impedance data bus

---

## Error Detection
The design checks for an invalid condition when both read and write are active simultaneously:

WE = 0 and OE = 0

If this occurs, an operational error message is displayed.

---

## Synthesis
The design is synthesized using the constraint file **ram_model.sdc**.  
The synthesis process generates:

- Gate-level netlist
- Area report
- Timing report
- Power report

---

## Generated Reports

Area Report → ram_model_area.rpt  
Timing Report → ram_model_timing.rpt  
Power Report → ram_model_power.rpt  

These reports help evaluate the hardware resource usage and performance of the design.

---

## Applications
- Embedded systems
- Digital processors
- Memory subsystem design
- FPGA prototyping
- ASIC design verification

---

## Author
Verilog HDL project demonstrating **RAM design, simulation, synthesis, and report generation**.
