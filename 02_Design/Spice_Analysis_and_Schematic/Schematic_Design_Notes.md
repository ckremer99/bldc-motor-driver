# Schematic Design Notes
**Document ID:** BLDC-DES-001
**Tool:** KiCad (schematic capture)

## 1. Functional Block Diagram
[Sketch/describe the blocks: input EMI filter → power stage (3-phase bridge) → gate drivers → MOSFETs → motor phases; Hall sensor input → commutation logic → PWM control; current sense → protection.]

## 2. Design Decisions Log
Record each significant choice and *why*, not just what — this is the part that reads well in an interview.

| Date | Decision | Rationale | Alternatives Considered |
|---|---|---|---|
| | e.g. Chose gate driver IC X over Y | | |
| | e.g. Chose MOSFET with Vds rating of __ | | |

## 3. Key Circuit Blocks

### 3.1 Power Stage (3-Phase Bridge)
[MOSFET selection criteria, bootstrap/gate drive topology, dead-time considerations.]

### 3.2 Gate Drive
[IC chosen, isolation (if any), bootstrap capacitor sizing.]

### 3.3 Current Sensing
[Shunt vs. hall-effect sensor choice, amplifier gain, filtering.]

### 3.4 Hall Sensor Interface
[Pull-ups, filtering, debounce if needed.]

### 3.5 Protection Circuits
[Overcurrent, undervoltage lockout, reverse polarity, TVS/flyback protection.]

## 4. Bill of Materials Rationale
[For critical parts, note why selected: cost, availability, lifecycle status, package.]
