# Interface Control Document (ICD)
**Document ID:** BLDC-ICD-001
**Revision:** A
**Date:** Aug 26-2026

## 1. Purpose
Defines every electrical and mechanical interface this board presents to the outside world (power source, motor, host controller, test equipment).

## 2. Connector Pinout
- Define driver requirements before proceeding. 

### J1 — DC Power Input
| Pin | Signal | Description | Rating |
|---|---|---|---|
| 1 | VIN+ | | |
| 2 | VIN- / GND | | |

### J2 — Motor Phase Output
| Pin | Signal | Description | Rating |
|---|---|---|---|
| 1 | Phase A | | |
| 2 | Phase B | | |
| 3 | Phase C | | |

### J3 — Hall Sensor Input
| Pin | Signal | Description | Rating |
|---|---|---|---|
| 1 | Hall A | | |
| 2 | Hall B | | |
| 3 | Hall C | | |
| 4 | Hall VCC | | |
| 5 | Hall GND | | |

### J4 — Control/Command Interface
| Pin | Signal | Description | Rating |
|---|---|---|---|
| 1 | Speed Command | | |
| 2 | Enable | | |
| 3 | Fault Output | | |
| 4 | GND | | |

## 3. Electrical Interface Definitions
[Signal-by-signal: voltage levels, logic thresholds, timing, source/sink impedance.]

## 4. Mechanical Interface
[Board outline dimensions, mounting hole pattern, connector keying/orientation.]

## 5. Grounding Scheme
[Single-point ground? Power vs. signal ground separation? Chassis bond point?]

## Research Notes and Sources

