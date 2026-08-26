# Thermal Analysis
**Document ID:** BLDC-THERM-001

## 1. Power Dissipation Estimates
| Component | Conduction Loss | Switching Loss | Total | Basis/Formula |
|---|---|---|---|---|
| Main MOSFETs (each) | | | | Pcond = Irms² × Rds(on); Psw = f_sw × E_sw |
| Gate driver IC | | | | |
| Current sense shunt | | | | |

## 2. Junction Temperature Calculation
[For the highest-dissipation part: Tj = Ta + P × θJA (or θJC + θCA if heatsinked). Show the math.]

## 3. Heatsinking Decision
[Do you need a heatsink/thermal pad given the Tj result and max ambient? What margin are you targeting?]

## 4. Verification Plan
[Thermal camera or thermocouple measurement plan for bring-up, to check against this calculation.]
