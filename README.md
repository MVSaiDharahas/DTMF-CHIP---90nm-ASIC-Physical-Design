# DTMF_CHIP — 90nm ASIC Physical Design

> End-to-end ASIC Physical Design implementation of the hierarchical `DTMF_CHIP` design using Cadence Innovus.

## Project Overview

This project demonstrates the physical implementation and signoff-oriented analysis of a hierarchical 90nm DTMF ASIC design using the Cadence Innovus implementation flow.

The design was taken through the major backend stages:

```text
Design Initialization
        ↓
MMMC / SDC Constraints
        ↓
Floorplanning
        ↓
Power Planning
        ↓
Placement
        ↓
Pre-CTS Optimization
        ↓
Clock Tree Synthesis (CTS)
        ↓
Post-CTS Optimization
        ↓
Routing
        ↓
Post-Route Analysis
        ↓
Timing / Power / Congestion / Parasitic Analysis
```

The project focuses on practical Physical Design concepts including floorplanning, macro placement, power distribution, standard-cell placement, CTS, routing, STA, clock analysis, congestion, density, power and parasitic analysis.

---

## Design Hierarchy

```text
DTMF_CHIP
│
├── DTMF_INST
│   │
│   ├── ARB_INST
│   ├── DATA_SAMPLE_MUX_INST
│   ├── DIGIT_REG_INST
│   ├── DMA_INST
│   ├── RAM_128x16_TEST_INST
│   ├── RAM_256x16_TEST_INST
│   ├── RESULTS_CONV_INST
│   ├── SPI_INST
│   │
│   ├── TDSP_CORE_INST
│   │   ├── ACCUM_STAT_INST
│   │   ├── ALU_32_INST
│   │   ├── DATA_BUS_MACH_INST
│   │   ├── DECODE_INST
│   │   ├── EXECUTE_INST
│   │   ├── MPY_32_INST
│   │   │   └── M16X16_INST
│   │   ├── PORT_BUS_MACH_INST
│   │   ├── PROG_BUS_MACH_INST
│   │   ├── TDSP_CORE_GLUE_INST
│   │   └── TDSP_CORE_MACH_INST
│   │
│   ├── TDSP_DS_CS_INST
│   ├── TDSP_MUX
│   ├── TEST_CONTROL_INST
│   └── ULAW_LIN_CONV_INST
│
└── IOPADS_INST
```

### Major Functional Blocks

| Block | Function |
|---|---|
| `ARB_INST` | Arbitration and control logic |
| `DATA_SAMPLE_MUX_INST` | Data sampling and multiplexing |
| `DIGIT_REG_INST` | Digit/register logic |
| `DMA_INST` | Direct Memory Access logic |
| `RAM_128x16_TEST_INST` | 128 × 16 memory/test block |
| `RAM_256x16_TEST_INST` | 256 × 16 memory/test block |
| `RESULTS_CONV_INST` | Result conversion logic |
| `SPI_INST` | Serial Peripheral Interface |
| `TDSP_CORE_INST` | Main DSP processing core |
| `ACCUM_STAT_INST` | Accumulation/status logic |
| `ALU_32_INST` | 32-bit ALU |
| `DATA_BUS_MACH_INST` | Data bus control logic |
| `DECODE_INST` | Instruction decode logic |
| `EXECUTE_INST` | Instruction execution logic |
| `MPY_32_INST` | 32-bit multiplier |
| `M16X16_INST` | 16 × 16 multiplier |
| `PORT_BUS_MACH_INST` | Port bus control logic |
| `PROG_BUS_MACH_INST` | Program bus control logic |
| `TDSP_CORE_GLUE_INST` | Core interface/glue logic |
| `TDSP_CORE_MACH_INST` | Core machine/control logic |
| `TDSP_DS_CS_INST` | Data/control selection logic |
| `TDSP_MUX` | Multiplexing logic |
| `TEST_CONTROL_INST` | Test-mode control |
| `ULAW_LIN_CONV_INST` | μ-law to linear conversion |
| `IOPADS_INST` | I/O pad structures |

---

## Technology and Tools

| Parameter | Details |
|---|---|
| Design | `DTMF_CHIP` |
| Technology | 90nm |
| Implementation Tool | Cadence Innovus |
| Innovus Version | 20.11-s130_1 |
| OS | Linux x86_64 |
| Timing Methodology | MMMC |
| Variation Analysis | OCV |
| Parasitics | SPEF / RCDB |
| Scripting | Tcl |

---

# Physical Design Flow

## 1. Design Initialization

- Loaded the design database and technology information.
- Initialized standard-cell, macro and I/O information.
- Configured timing and analysis views.
- Prepared the design for physical implementation.

**GUI:**

<!-- Add initialization screenshot here -->

---

## 2. Floorplanning

The floorplanning stage established:

- Die/core dimensions
- Core utilization
- I/O pad locations
- Macro locations
- Placement regions
- Routing resources
- Physical design boundaries

The design contains several large memory and PLL-related macro blocks.

**GUI:**

<!-- Add floorplan screenshot here -->

![Floorplan](images/floorplan.png)

---

## 3. Power Planning

The power distribution network was implemented around the core and macro regions.

The power-planning stage included:

- Power rings
- Power stripes
- Standard-cell power rails
- Power connections
- Macro power connectivity
- Power vias

**GUI:**

<!-- Add power-plan screenshot here -->

![Power Plan](images/powerplan.png)

---

## 4. Standard-Cell Placement

The standard cells were placed around the hard macros while considering:

- Timing
- Congestion
- Density
- Macro accessibility
- Routing resources
- Placement legality

**GUI:**

<!-- Add placement screenshot here -->

![Placement](images/placement.png)

---

## 5. Clock Tree Synthesis

Two major clock domains were analyzed:

```text
vclk1
vclk2
```

CTS analysis included:

- Clock latency
- Clock skew
- Clock jitter
- Clock balance
- Inter-clock skew
- Launch/capture latency

**GUI:**

<!-- Add CTS screenshot here -->

![CTS](images/cts.png)

---

## 6. Routing

The routing stage included:

- Global routing
- Detailed routing
- Signal routing
- Clock routing
- Via insertion
- Post-route optimization
- Parasitic extraction/analysis

**GUI:**

<!-- Add routing screenshot here -->

![Routing](images/routing.png)

---

# Design Statistics

The implementation reports show the following post-implementation design statistics:

| Metric | Value |
|---|---:|
| Design | `DTMF_CHIP` |
| Total Instances | 6149 |
| DTMF Core Instances | 6077 |
| I/O Pad Instances | 72 |
| Total Reported Area | 1284833.181 |

---

# Clock Configuration

| Clock | Period | Frequency |
|---|---:|---:|
| `vclk1` | 7 ns | 142.86 MHz |
| `vclk2` | 14 ns | 71.43 MHz |

```text
Frequency = 1 / Clock Period

vclk1 = 1 / 7 ns
      ≈ 142.86 MHz

vclk2 = 1 / 14 ns
      ≈ 71.43 MHz
```

---

# Timing Analysis

## Setup Timing

Final timing summary:

```text
Setup WNS = +0.002 ns
Setup TNS =  0.000 ns
FEP       =  0
```

A representative setup path was reported with:

```text
Setup Slack = +0.002 ns
```

This indicates the analyzed worst setup path has a small positive timing margin.

---

## Hold Timing

During optimization, a significant hold violation was observed and subsequently improved.

### Earlier Analysis

```text
Hold Slack ≈ -1.99 ns
```

### Later Analysis

```text
Hold Slack = +0.002 ns
```

This demonstrates the effect of physical-design optimization on hold timing.

---

# Clock Tree Analysis

## `vclk1`

```text
Maximum Launch Latency  = 2.036 ns
Minimum Capture Latency = 0.497 ns
Maximum Skew            = 1.536 ns
```

## `vclk2`

```text
Maximum Launch Latency  = 0.440 ns
Minimum Capture Latency = -0.138 ns
```

## Inter-Clock Analysis

```text
Clock Relationship = vclk1 → vclk2
Inter-Clock Skew   = 2.166 ns
```

---

# Congestion Analysis

The routing congestion report showed:

```text
Horizontal Usage ≈ 11.4%
Vertical Usage   ≈ 12.6%

Horizontal Overflow = 54
Vertical Overflow   = 0
```

The congestion hotspot analysis reported:

```text
Maximum normalized hotspot area = 0.00
Total normalized hotspot area   = 0.00
```

---

# Density Analysis

```text
Density Threshold = 0.750
High-Density Bins = 123
Total Bins        = 256
High-Density Area = 48.05%

Density Unevenness Ratio = 9.517%
```

The density map was used to identify regions with high placement density.

**GUI:**

<!-- Add density-map screenshot here -->

![Density Map](images/density_map.png)

---

# Power Analysis

The reported total power was:

```text
Internal Power  = 76.6808
Switching Power = 7.3711
Leakage Power   = 0.004631
Total Power     = 84.0565
```

## Power Breakdown

| Group | Internal Power | Switching Power | Leakage Power | Total Power | Percentage |
|---|---:|---:|---:|---:|---:|
| Sequential | 6.477 | 0.5609 | 0.001265 | 7.039 | 8.374% |
| Macro | 46.02 | 0.1704 | 0 | 46.19 | 54.95% |
| I/O | 19.38 | 0.07096 | 0 | 19.45 | 23.14% |
| Combinational | 4.455 | 5.381 | 0.003316 | 9.839 | 11.70% |
| Clock (Combinational) | 0.350 | 1.188 | 0.00004939 | 1.538 | 1.83% |

### Rail-Level Power

```text
Default Rail Total Power ≈ 19.47
VDD Rail Total Power     ≈ 64.59
```

---

# Parasitic Analysis

The parasitic report showed:

```text
Total Nets               = 6926
Annotated Nets           = 6477
Annotated Percentage     = 93.52%
Not Annotated Nets       = 449
Not Annotated Percentage = 6.48%
```

Reported aggregate parasitic values:

```text
Resistance  ≈ 300.1749 KΩ
Capacitance ≈ 59.4472 pF
```

---

# Timing Coverage

| Check Type | Total Checks | Met | Violated | Untested |
|---|---:|---:|---:|---:|
| Clock Period | 6 | 6 (100%) | 0 | 0 |
| External Delay (Late) | 25 | 9 (36%) | 0 | 16 (64%) |
| Pulse Width | 1361 | 1088 (79%) | 0 | 273 (20%) |
| Recovery | 269 | 0 | 0 | 269 (100%) |
| Setup | 1821 | 219 (12%) | 0 | 1602 (87%) |

> Timing coverage is reported as generated by the Innovus analysis environment. Untested checks should be considered when evaluating complete signoff readiness.

---

# Fanout / DRV Analysis

The design showed maximum-fanout violations:

```text
Maximum Fanout WNS = -85.000
Maximum Fanout TNS = -1623.000
FEP                = 141
```

Potential optimization techniques include:

- Buffer insertion
- Fanout splitting
- Driver upsizing
- Placement optimization
- Logic restructuring

---

# Clock Checks

```text
Minimum Pulse Width WNS = +1.569 ns
Minimum Period WNS      = +3.709 ns
```

No violations were reported for the displayed minimum pulse-width and minimum-period checks.

---

# Representative Timing Paths

## Setup Path

```text
Startpoint:
DTMF_INST/RESULTS_CONV_INST/r1633_reg_13/CK

Endpoint:
DTMF_INST/RESULTS_CONV_INST/gt_reg/D

Clock:
vclk1

Setup Slack:
+0.002 ns
```

## Hold Path

```text
Startpoint:
DTMF_INST/RESULTS_CONV_INST/r1477_reg_0/CK

Endpoint:
DTMF_INST/RESULTS_CONV_INST/r1477_reg_0/D

Clock:
vclk2

Hold Slack:
+0.002 ns
```

---

# Physical Design Observations

The implementation provided practical exposure to the following backend challenges:

### Timing

- Setup and hold timing analysis
- Hold violation identification and optimization
- Cross-clock timing paths
- Clock latency and skew analysis
- Timing-path debugging

### Clock

- CTS
- Clock latency
- Clock skew
- Inter-clock skew
- Clock jitter
- Pulse-width checks

### Power

- Internal power
- Switching power
- Leakage power
- Macro power contribution
- Clock power contribution
- Rail-level power analysis

### Physical Implementation

- Macro placement
- Standard-cell placement
- Power-grid construction
- Routing
- Density analysis
- Congestion analysis
- Parasitic analysis

### Signoff-Oriented Analysis

- STA
- MMMC
- OCV
- Timing coverage
- Parasitic annotation
- Fanout/DRV analysis

---

# Innovus Reports Used

```tcl
report_area

report_congestion -hotspot -overflow

report_density_map

report_power

report_timing

report_timing_summary

report_timing -unconstrained

report_clock_timing -type latency

report_clock_timing -type skew

report_clock_timing -type jitter

report_clock_timing -type summary

report_clock_timing -type interclock_skew

report_analysis_coverage

report_annotated_delay

report_annotated_parasitics
```

---

# Project Structure

```text
DTMF-CHIP-Physical-Design/
│
├── README.md
│
├── scripts/
│   ├── init.tcl
│   ├── floorplan.tcl
│   ├── powerplan.tcl
│   ├── placement.tcl
│   ├── cts.tcl
│   ├── routing.tcl
│   └── reports.tcl
│
├── constraints/
│   ├── clocks.sdc
│   └── constraints.sdc
│
├── reports/
│   ├── area/
│   ├── timing/
│   ├── power/
│   ├── congestion/
│   ├── clock/
│   └── parasitics/
│
├── images/
│   ├── hierarchy.png
│   ├── floorplan.png
│   ├── powerplan.png
│   ├── placement.png
│   ├── cts.png
│   ├── routing.png
│   └── density_map.png
│
└── docs/
    └── project_notes.md
```

---

# Key Results

| Category | Result |
|---|---:|
| Technology | 90nm |
| Total Instances | 6149 |
| DTMF Core Instances | 6077 |
| I/O Pads | 72 |
| Total Reported Area | 1284833.181 |
| `vclk1` Period | 7 ns |
| `vclk1` Frequency | 142.86 MHz |
| `vclk2` Period | 14 ns |
| `vclk2` Frequency | 71.43 MHz |
| Setup WNS | +0.002 ns |
| Setup TNS | 0 ns |
| Later Hold Slack | +0.002 ns |
| Maximum `vclk1` Skew | 1.536 ns |
| `vclk1` Max Launch Latency | 2.036 ns |
| Inter-Clock Skew | 2.166 ns |
| Total Power | 84.0565 |
| Internal Power | 76.6808 |
| Switching Power | 7.3711 |
| Leakage Power | 0.004631 |
| Horizontal Overflow | 54 |
| Vertical Overflow | 0 |
| Parasitic Annotation | 93.52% |
| Max Fanout WNS | -85.000 |
| Max Fanout TNS | -1623.000 |
| Fanout FEP | 141 |

---

# Skills Demonstrated

```text
ASIC Physical Design
Cadence Innovus
90nm ASIC Implementation
Floorplanning
Macro Placement
Power Planning
Standard-Cell Placement
Placement Optimization
Clock Tree Synthesis
Clock Skew Analysis
Clock Latency Analysis
Clock Jitter Analysis
Global Routing
Detailed Routing
Static Timing Analysis
Setup Analysis
Hold Analysis
MMMC
OCV
Congestion Analysis
Density Analysis
Power Analysis
Parasitic Analysis
Timing Coverage
Fanout / DRV Analysis
Tcl Scripting
Physical Design Automation
```

---

# Project Highlights

- Implemented a hierarchical 90nm ASIC physical-design flow using Cadence Innovus.
- Worked with a multi-block design containing DSP logic, memory macros, SPI, DMA and I/O structures.
- Performed floorplanning and macro placement for a macro-rich design.
- Implemented power distribution planning with rings, stripes, rails and vias.
- Performed standard-cell placement and congestion analysis.
- Built and analyzed clock trees for multiple clock domains.
- Investigated setup and hold timing paths using detailed timing reports.
- Improved an observed hold violation from approximately `-1.99 ns` to `+0.002 ns` in later analysis.
- Performed post-route power, parasitic, timing, density and congestion analysis.
- Used Tcl/Innovus reporting commands for implementation analysis and automation.

---

# Conclusion

This project demonstrates a practical ASIC Physical Design implementation of the `DTMF_CHIP` design using Cadence Innovus.

The work covers the major backend implementation stages from floorplanning through routing and extends into signoff-oriented analysis of:

```text
Area
Timing
Power
Clock
Congestion
Density
Routing
Parasitics
Fanout
Design Rules
```

The project is intended to demonstrate hands-on understanding of the ASIC Physical Design flow and the trade-offs between timing, power, area and physical implementation constraints.
