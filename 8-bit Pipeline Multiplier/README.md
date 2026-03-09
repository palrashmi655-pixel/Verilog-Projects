# 8-bit Pipelined Multiplier (Two's Complement) using Verilog

## Overview
This project implements an **8-bit pipelined multiplier for two's complement numbers** using **Verilog HDL**.  
The design multiplies two signed 8-bit inputs and produces a **16-bit signed output**.

The multiplier uses **pipeline stages** to improve throughput and allow high-speed operation in digital systems.

The project also includes **synthesis constraints, generated netlist, and synthesis reports (area, timing, power)**.

---

## Features
- 8-bit signed multiplication (Two's Complement)
- Pipelined architecture
- 16-bit output
- Verilog HDL implementation
- Synthesis using timing constraints
- Area, timing, and power report generation

---

## Pipeline Operation
The multiplier uses **8 pipeline stages**.  
Each clock cycle shifts intermediate values through pipeline registers.

Pipeline flow:

```
Stage 0 → Input Capture
Stage 1 → Partial computation
Stage 2 → Pipeline shift
Stage 3 → Pipeline shift
Stage 4 → Pipeline shift
Stage 5 → Pipeline shift
Stage 6 → Pipeline shift
Stage 7 → Output stage
```

The output result appears **after 8 clock cycles**.

---

## Project Files

```
project/
│
├── pipe.v            # Verilog design of pipelined multiplier
├── pipe_test.v       # Testbench for simulation
├── pipe.sdc          # Synthesis timing constraints
│
├── pipe_netlist.v    # Synthesized gate-level netlist
│
├── pipe_area.rpt     # Area report
├── pipe_timing.rpt   # Timing report
├── pipe_power.rpt    # Power report
```

---

## Module Description

### Top Module
`mult_piped_8x8_2sC`

**Inputs**
- `a[7:0]` → 8-bit signed input
- `b[7:0]` → 8-bit signed input
- `clk` → Clock signal
- `reset` → Reset signal

**Output**
- `y[15:0]` → 16-bit multiplication result

---

## Multiplication Method

The design performs **signed multiplication using magnitude conversion**.

Steps:
1. Extract magnitude of both numbers.
2. Multiply magnitudes.
3. Determine sign using XOR of sign bits.
4. Convert result back to two's complement if negative.

---

## Simulation

The design is verified using the **testbench (`pipe_test.v`)**.

Example:

```
a = 8'b00001010  (10)
b = 8'b00000101  (5)

Output:
y = 16'b0000000000110010  (50)
```

Waveforms confirm correct pipelined operation.

---

## Synthesis

The design is synthesized using a **timing constraint file (`pipe.sdc`)**.

The synthesis tool generates:

- Gate-level netlist
- Area report
- Timing report
- Power report

---

## Generated Reports

### Area Report
`pipe_area.rpt`

Shows:
- Cell utilization
- Logic area

### Timing Report
`pipe_timing.rpt`

Shows:
- Critical path delay
- Setup/hold timing

### Power Report
`pipe_power.rpt`

Shows:
- Dynamic power
- Leakage power

---

## Applications
- Digital Signal Processing (DSP)
- Arithmetic Logic Units (ALU)
- Embedded processors
- Image processing systems
- High-speed arithmetic circuits

---

## Author
Digital Design Project implemented using **Verilog HDL** to demonstrate **pipelined signed multiplication and synthesis flow with report generation**.
