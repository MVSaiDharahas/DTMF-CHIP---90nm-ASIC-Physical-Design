# DTMF CHIP - 90nm ASIC Physical Design

## Complete RTL-to-Post-Route Physical Design Implementation using Cadence Innovus

![Technology](https://img.shields.io/badge/Technology-90nm-blue)
![EDA Tool](https://img.shields.io/badge/EDA-Cadence%20Innovus-red)
![Flow](https://img.shields.io/badge/Flow-RTL%20to%20Post--Route-green)
![Scripting](https://img.shields.io/badge/Scripting-Tcl-orange)
![Analysis](https://img.shields.io/badge/Analysis-MMMC%20%7C%20OCV-purple)

---

## 📌 Project Overview

This project presents the **ASIC Physical Design implementation of a DTMF (Dual-Tone Multi-Frequency) chip** using **Cadence Innovus 20.11-s130_1** in a **90nm technology environment**.

The design was taken through the major backend implementation stages, including:

- Design initialization
- Floorplanning
- I/O and macro planning
- Power planning
- Standard-cell placement
- Placement optimization
- Clock Tree Synthesis (CTS)
- Routing
- Post-route timing analysis
- Clock latency and skew analysis
- Power analysis
- Congestion analysis
- Parasitic analysis
- Timing-check coverage analysis
- Design-rule and fanout analysis
- Tcl-based reporting and automation

The project focuses on understanding the interaction between **area, timing, power, congestion, clock distribution, routing and physical constraints** during ASIC implementation.

---

# 🎯 Objectives

The main objectives of this project were:

- Perform physical implementation of a complex hierarchical ASIC design.
- Develop a practical floorplan containing standard cells, I/O structures and embedded memory macros.
- Create a power-distribution network for the design.
- Perform standard-cell placement and optimization.
- Implement clock trees for multiple clock domains.
- Analyze clock latency, skew and jitter.
- Perform global and detailed routing.
- Analyze post-route setup and hold timing.
- Analyze power consumption and leakage.
- Analyze placement and routing congestion.
- Analyze extracted parasitics.
- Evaluate timing-check coverage.
- Identify timing and design-rule violations.
- Use Tcl scripting to automate implementation and reporting tasks.

---

# 🏗️ Design Information

| Parameter | Details |
|---|---|
| Design | DTMF_CHIP |
| Application | DTMF Processing |
| Technology | 90nm |
| Physical Design Tool | Cadence Innovus |
| Innovus Version | 20.11-s130_1 |
| Operating System | Linux x86_64 |
| Timing Analysis | MMMC / OCV |
| Parasitic Analysis | SPEF / RCDB |
| Scripting | Tcl |
| Clock Domains | vclk1, vclk2 |

---

# 🔄 Physical Design Flow

```text
                    DTMF CHIP
                        │
                        ▼
              Design Initialization
                        │
                        ▼
                MMMC / SDC Setup
                        │
                        ▼
                  Floorplanning
                        │
                        ▼
              I/O & Macro Placement
                        │
                        ▼
                 Power Planning
                        │
                        ▼
             Standard Cell Placement
                        │
                        ▼
              Placement Optimization
                        │
                        ▼
             Pre-CTS Optimization
                        │
                        ▼
          Clock Tree Synthesis (CTS)
                        │
                        ▼
                     Routing
                        │
                        ▼
               Post-Route Analysis
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
       Timing         Power        Physical
          │             │             │
     Setup/Hold     Internal       Area
     WNS/TNS        Switching      Density
     Clock Skew     Leakage        Congestion
     Latency        Clock Power    Parasitics
     Jitter
```

