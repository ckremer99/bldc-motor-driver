# SPICE Analysis
**Document ID:** BLDC-SPICE-001
**Tool:** LTspice

## 1. Purpose
Pre-layout verification of critical circuit behavior via simulation, before committing to hardware.

## 2. Simulations Performed

### 2.1 Gate Drive Switching
- **Goal:** verify gate drive rise/fall time, verify no shoot-through with chosen dead time
- **Circuit:** [link/screenshot]
- **Result:** [waveform, key numbers]
- **Pass/Fail vs. requirement:** [reference REQ-### if applicable]

### 2.2 Current Sense Path
- **Goal:** verify shunt amplifier output scaling and bandwidth across expected current range
- **Result:**

### 2.3 [Add more as needed: snubber design, bootstrap capacitor droop, input filter response, etc.]

## 3. Model Limitations / Assumptions
[Note anything simplified in the sim that real hardware won't match — e.g., ignored parasitic PCB inductance, ideal component models — so you remember to double check these at bring-up.]
