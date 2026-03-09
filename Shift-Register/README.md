# Parameterized Shifter using Verilog HDL

## Overview
This project implements a **parameterized shift register (Shifter)** using **Verilog HDL**. The design supports **serial shifting, serial output, and parallel loading** operations controlled by enable and write signals.

The project demonstrates the **digital design flow including Verilog implementation, synthesis, and report generation** such as **area, timing, and power reports**.

---

## Features
- Parameterized shift register
- Configurable register length
- Serial input and serial output
- Parallel data loading
- High impedance data bus when inactive
- Verilog HDL implementation
- Synthesis report generation (Area, Timing, Power)

---

## Shifter Architecture

The design uses a **right shift register**.

Shift operation performed on every positive clock edge:

```
Reg = Reg >> 1
Reg[Length-1] = SI
```

This shifts the register right and inserts the **serial input (SI)** at the most significant bit.

---

## Project Files

```
project/

SHIFTER.v            → Verilog design of the shifter
shifter_netlist.v    → Synthesized gate-level netlist

shifter_area.rpt     → Area report
shifter_timing.rpt   → Timing report
shifter_power.rpt    → Power report
```

---

## Module Description

### Top Module
`Shifter`

### Parameter
`Length` → Size of the shift register

### Inputs
- `Clk` → Clock signal  
- `EN` → Enable shift operation  
- `WR` → Write enable (parallel load)  
- `RD` → Read enable  
- `SI` → Serial input  

### Outputs
- `SO` → Serial output  

### Inout
- `Data[Length-1:0]` → Parallel data bus

---

## Operation

### Shift Operation
Shifting occurs when:

```
EN = 0
```

Actions performed:
1. Least significant bit becomes **serial output**
2. Register shifts right
3. Serial input enters the MSB

---

### Parallel Load Operation
Parallel loading occurs when:

```
WR = 0
EN = 1
```

The data present on the **Data bus** is loaded into the shift register.

---

### Read Operation
When read is enabled:

```
RD = 0
```

The register contents are placed on the **Data bus**.

---

### High Impedance State
When read is disabled:

```
Data = Z
```

The bus enters a **high impedance state**.

---

## Error Detection
The design checks for an invalid condition:

```
WR = 0 and EN = 0
```

If both write and enable are active simultaneously, an **error message** is generated.

---

## Synthesis
After synthesis the following outputs are generated:

- **Gate-level netlist**
- **Area report**
- **Timing report**
- **Power report**

These reports help evaluate **hardware usage and performance**.

---

## Generated Reports

- `shifter_area.rpt` → Area utilization  
- `shifter_timing.rpt` → Timing analysis  
- `shifter_power.rpt` → Power consumption  

---

## Applications
- Serial communication systems
- Data shifting operations in processors
- Digital signal processing
- FPGA and ASIC implementations
- Data buffering systems

---

## Author
Verilog HDL project demonstrating **shift register design, synthesis, and hardware report generation**.
