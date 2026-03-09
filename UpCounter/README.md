# 4-Bit Asynchronous Up Counter using Verilog HDL

## Overview
This project implements a **4-bit asynchronous (ripple) up counter** using **Verilog HDL**. The design uses **T Flip-Flops** connected in cascade where each stage is triggered by the output of the previous flip-flop. The counter increments its value on each clock cycle.

The project demonstrates the **complete digital design flow**, including Verilog implementation, simulation, synthesis with timing constraints, and generation of **area, timing, and power reports**.

---

## Features
- 4-bit asynchronous ripple counter
- Implemented using T Flip-Flops
- Negative edge triggered operation
- Reset functionality
- Verilog HDL implementation
- Synthesis with timing constraints
- Area, timing, and power report generation

---

## Counter Architecture

The counter is built using **four T Flip-Flops** connected in series.

Clock flow:

```
Clock → TFF0 → TFF1 → TFF2 → TFF3
```

Each flip-flop toggles when the previous stage output changes, producing a ripple counting effect.

Counting sequence:

```
0000
0001
0010
0011
0100
0101
0110
0111
1000
...
1111
```

---

## Project Files

```
project/

upCount.v → Verilog implementation of the up counter
upCount_test.v → Testbench for simulation
Upcounter.sdc → Timing constraint file

Upcounter_netlist.v → Synthesized gate-level netlist

Upcounter_area.rpt → Area report
Upcounter_timing.rpt → Timing report
Upcounter_power.rpt → Power report
```

---

## Module Description

### T Flip-Flop Module
`tff`

Inputs:
- `clk` → Clock signal
- `reset` → Reset signal

Output:
- `q` → Flip-flop output

Operation:
- On the **negative edge of the clock**, the output toggles.
- If **reset is active**, the output becomes `0`.

---

### Asynchronous Up Counter Module
`async_up_counter`

Inputs:
- `clk` → Clock signal
- `reset` → Reset signal

Outputs:
- `count[3:0]` → 4-bit counter output

Each flip-flop uses the **previous flip-flop output as its clock input**, creating the ripple counter.

---

## Operation

1. The first flip-flop toggles with the external clock.
2. Each subsequent flip-flop toggles when the previous stage output changes.
3. The counter increases its value in binary sequence.
4. When reset is active, the counter returns to:

```
0000
```

---

## Simulation
The design is verified using the **testbench (`upCount_test.v`)**.

Simulation checks:
- Correct binary counting sequence
- Reset functionality
- Clock-driven toggling

---

## Synthesis
The design is synthesized using the constraint file **Upcounter.sdc**.

Synthesis generates:

- Gate-level netlist
- Area utilization report
- Timing analysis report
- Power consumption report

---

## Generated Reports

Area Report → Upcounter_area.rpt  
Timing Report → Upcounter_timing.rpt  
Power Report → Upcounter_power.rpt  

These reports evaluate the **hardware utilization and performance of the counter**.

---

## Applications
- Digital clocks
- Frequency dividers
- Event counting systems
- Embedded timers
- FPGA and ASIC digital designs

---

## Author
Verilog HDL project demonstrating **asynchronous counter design, simulation, synthesis, and hardware report generation**.
