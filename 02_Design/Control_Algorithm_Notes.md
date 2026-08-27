# Control Algorithm Design Notes
**Document ID:** BLDC-CTRL-001
**Tool:** Simulink (or documented equivalent)

## 1. Commutation Scheme
Commutation will take place using a 3-phase inverter. Trapasoidal waveform where voltage level is determined by PWM of switches. Feedback will be provided through ADC voltage measurements of inactive phase (back emf). 


## 2. Speed Control Loop - Rev A

- Input Thrust Command 
- Plant: Propeller RPM (related to thrust in a non-linear way)
- Process: PWM 3-phase waveform generator. 
- Feedback Path A: Back EMF frequency measurements will calculate true RPM for rotors. This will be fed back into uC on driver board. 
- Feedback Path B: thrust measurements from accelerometer on main board. 

- **Loop type Rotor Speed:** Because rotors have small inertia, the loop will be primarily PI. We want zero steady-state error while the system is responsive to rapid changes in speed command. 

- **Loop type Acceleration Command:** Since thrust for each prop can be calculated from XYZ components of accelerometer, and accuracy of feedback from acceleometer is limited, simple proportional control for acceleration would be suitable since true error has some inhearant uncertainty (unless if expensive LIDAR was used or some more accurate measurement of acceleration). 

- **Block diagram:** 
![block diagram acc](images/block_diagram_acc_control.png)


- **Tuning approach:** [analytical vs. empirical — record gains and how you got them]
- **Model results:**: Due to thrust being non-linear we will use an adaptive state-space model

## 3. Protection Logic
[How overcurrent/UVLO faults interrupt PWM output — latched vs. auto-retry.]

## 4. Open Questions / Risks
[Anything you're unsure about going into hardware — e.g., "commutation timing margin at max speed is untested in sim."]
