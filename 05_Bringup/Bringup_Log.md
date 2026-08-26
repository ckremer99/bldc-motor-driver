# Bring-up Log
**Document ID:** BLDC-BU-001

*Log entries chronologically — this becomes your "how I debug" evidence for interviews.*

## Pre-Power Checklist
- [ ] Visual inspection for solder shorts/defects
- [ ] Continuity check of critical nets vs. schematic
- [ ] Confirm no shorts across power rails (multimeter, board unpowered)

## Power-Up Sequence
| Step | Action | Expected Result | Actual Result | Pass/Fail |
|---|---|---|---|---|
| 1 | Apply VIN via current-limited supply, limit set to __ mA | No excess current draw | | |
| 2 | Measure logic rail voltage | __ V ± __ % | | |
| 3 | Measure gate driver Vcc | | | |

## Block-by-Block Functional Bring-up
### Gate Drive
[Scope captures, waveform notes]

### Hall Sensor Interface
[Verify signals with motor hand-rotated]

### Commutation / Open-Loop Spin
[First successful spin — note conditions]

### Closed-Loop Speed Control
[Step response, stability]

### Protection Circuits
[Deliberately trigger OC/UVLO and confirm response]

## Issues Encountered
| Date | Issue | Root Cause | Fix |
|---|---|---|---|
| | | | |
