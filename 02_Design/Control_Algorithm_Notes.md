# Control Algorithm Design Notes
**Document ID:** BLDC-CTRL-001
**Tool:** Simulink (or documented equivalent)

## 1. Commutation Scheme
[Six-step trapezoidal commutation table: Hall state → active phases → PWM pattern.]

| Hall State (A,B,C) | Phase High | Phase Low | Phase Off |
|---|---|---|---|
| | | | |

## 2. Speed Control Loop
- **Loop type:** [e.g., single PI loop on speed, commanding PWM duty cycle]
- **Block diagram:** [describe/link]
- **Tuning approach:** [analytical vs. empirical — record gains and how you got them]
- **Model results:** [step response, settling time, overshoot from Simulink]

## 3. Protection Logic
[How overcurrent/UVLO faults interrupt PWM output — latched vs. auto-retry.]

## 4. Open Questions / Risks
[Anything you're unsure about going into hardware — e.g., "commutation timing margin at max speed is untested in sim."]
