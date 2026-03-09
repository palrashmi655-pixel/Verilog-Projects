# Universal Asynchronous Receiver (UAR) using Verilog HDL

## Overview
This project implements a **Universal Asynchronous Receiver (UAR)** using **Verilog HDL**. The design receives **serial data** and converts it into **8-bit parallel data** while generating status signals such as **data ready** and **data error**.

The project demonstrates the **complete digital design flow**, including Verilog implementation, simulation, synthesis using timing constraints, and generation of **area, timing, and power reports**.

---

## Features
- Serial to parallel data conversion
- Start bit detection
- Data ready and error flag generation
- 8-bit data reception
- Modular Verilog design
- Synthesis with timing constraints
- Area, timing, and power report generation

---

## Receiver Architecture

The Universal Asynchronous Receiver is built using several modules:

- **Start Detector** – Detects the start bit of incoming serial data
- **Counter** – Controls the timing and bit counting
- **Serial to Parallel Converter** – Converts serial input to 8-bit parallel output
- **Flags Module** – Generates ready and error signals
- **Control Module** – Manages receiver operation
- **Top Module (uar)** – Integrates all submodules

Data flow:

Serial Input → Start Detection → Bit Counting → Serial-to-Parallel Conversion → Output Data + Flags

---

## Project Files

project/

uar.v → Verilog implementation of the receiver  
uar_test.v → Testbench for simulation  
uar.sdc → Timing constraint file  

uar_netlist.v → Synthesized gate-level netlist  

uar_area.rpt → Area report  
uar_timing.rpt → Timing report  
uar_power.rpt → Power report  

---

## Module Description

### Top Module
`uar`

### Inputs
clk → Clock signal  
gl_reset → Global reset  
dIn → Serial data input  

### Outputs
dOut[7:0] → 8-bit parallel data output  
dReady → Indicates valid received data  
dError → Indicates reception error  

---

## Submodules

### Start Detect
Detects the **start bit** of incoming serial data using a shift register.

### Counter
Counts clock cycles and controls data sampling intervals.

### Serial to Parallel Converter
Converts incoming serial bits into **8-bit parallel data**.

### Flags
Generates:
- **dReady** → Data successfully received
- **dError** → Error detected in received data

### Control
Controls the **receiver running state** and overall data reception process.

---

## Operation

1. **Start Detection**
   The receiver detects the **start bit** in the incoming serial data stream.

2. **Bit Counting**
   The counter tracks clock cycles to determine when to sample bits.

3. **Data Conversion**
   The serial input bits are shifted into an **8-bit register**.

4. **Completion**
   After receiving 8 bits, the system sets:
   - `dReady` if data is valid
   - `dError` if an error occurs

---

## Simulation
The receiver behavior is verified using a **testbench (`uar_test.v`)**.

Simulation validates:
- Start bit detection
- Serial data reception
- Parallel data output
- Ready and error flag functionality

---

## Synthesis
The design is synthesized using the constraint file **uar.sdc**.

Synthesis generates:

- Gate-level netlist
- Area utilization report
- Timing analysis report
- Power consumption report

---

## Generated Reports

Area Report → uar_area.rpt  
Timing Report → uar_timing.rpt  
Power Report → uar_power.rpt  

These reports evaluate the **hardware resource usage and performance of the receiver design**.

---

## Applications
- UART communication systems
- Serial communication interfaces
- Embedded system communication
- FPGA and ASIC serial receivers
- Digital communication systems

---

## Author
Verilog HDL project demonstrating **Universal Asynchronous Receiver design, simulation, synthesis, and report generation**.
