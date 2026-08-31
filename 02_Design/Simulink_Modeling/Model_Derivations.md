

# Model Derivations

The objective of the simulink model is to determine the behavior of the drone acceleration in terms of the electrical inputs. 

## Equations Governing BLDC Motor Behavior

![bldc motor mechanical model](images/electromechanical_model_of_motor.png)

$$
u_a = R • i_a + L\frac{di_a}{dt} + e_a \\[1.5ex]
u_b = R • i_b + L\frac{di_b}{dt} + e_b \\[1.5ex]
u_c = R • i_c + L\frac{di_c}{dt} + e_c
$$

Rearranging gives: 

$$
\frac{di_a}{dt}=\frac{1}{L}(u_a-R\,i_a-e_a) \\[1.5ex]
\frac{di_b}{dt}=\frac{1}{L}(u_b-R\,i_b-e_b) \\[1.5ex]
\frac{di_c}{dt}=\frac{1}{L}(u_c-R\,i_c-e_c)
$$

These equations show the voltage at the stator winding accounting for the resistive losses of the coil, the stator inductance, and the back-emf. 

$$
\begin{align}
e_A &= K_w • f(θ_e) \,•\, ω \\
e_B &= K_w • f(θ_e - \frac{2π}{3})\,•\, ω \\
e_C &= K_w • f(θ_e + \frac{2π}{3})\,•\,ω
\end{align}
$$

### Electromagnetic Torque

The electromagnetic torque is found from the power balance between the electrical and mechanical domains: $e_A i_a + e_B i_b + e_C i_c = T_e\,ω$. Substituting the back-emf equations above, the $ω$ terms cancel, leaving torque as a function of rotor position and phase currents only (no division by $ω$, which avoids a singularity at standstill):

$$
T_e = K_w\Big(f(θ_e)\,i_a + f(θ_e - \tfrac{2π}{3})\,i_b + f(θ_e + \tfrac{2π}{3})\,i_c\Big)
$$

Accounting for mechanical torque: 

$$
T_{e}=T_{load}+J\,\frac{dω}{dt} + b\,ω \\[1.5ex]
\frac{d\omega}{dt}=\frac{1}{J}(T_e-T_{load}-b\,\omega)
$$



### Parameters Needed

|Parameter Name|Symbol|Unit|
|---|---|---|
|Winding Resistance|$R$|$\Omega$|
|Winding Inductance|$L$|$H$|
|Back-EMF Constant|$K_w$|$V/(rad/s)$|
|Viscous Damping Coefficient|$b$|$N•m/(rad/s)$|
|Rotor Inertia|$J$|$\text{kg}•m^2$

### Finding Parameter Estimates

R is not provided by the datasheet so we will need to estimate using similar motors. I will search for typical winding resistance for 1700 KV motor. We can estimate the breakdown for losses in the motor using the efficiency (which is specified). 

I had Claude do a search for similar motors: This is what it output: 

1. BrotherHobby Avenger 2806.5 Motor - 870KV/1300KV/1460KV/1700KV (https://www.getfpv.com/brotherhobby-avenger-2806-5-1300kv-1700kv-motor.html) — GetFPV product listing, source for R ≈ 44.3 mΩ (0.0443 Ω) on the specific 1700 KV Avenger 2806.5.
2. XRotor 2807 FPV Motors (1300KV/1500KV/1700KV) (https://www.hobbywing.com/en/products/-xrotor2807) — Hobbywing's own product page, used as a cross-check against a comparable-size motor family: 1300KV→60 mΩ, 1500KV→55 mΩ, 1700KV→50 mΩ.

Both landed in the same 44–50 mΩ range for a 1700 KV motor of this frame size, which is what gave R ≈ 0.044–0.05 Ω. 

We will use $R=0.05\Omega$

For $L$ the most reliable source was a forum (😬). [Link](https://community.st.com/stm32-mcus-motor-control-34/br2804-motor-1700kv-1-parameters-or-datasheet-i-am-using-p-nuncleo-ihm001-package-nucleo-f302r8-stspin-l6230-motor-driver-br2804-motor-1700kv-1-to-performance-foc-algorithm-23920)

The user used a calucaltor to estimate a 1700 KV motor to be around $L=0.018\:mH$.

Claude Cross-Check: Typical phase-to-phase inductance for a common 1700KV brushless (BLDC) motor—such as a 2207 or 2306 size drone motor—ranges between 3 µH and 15 µH (microhenries).

Let's use $L=9 \mu H$ by taking the average of the range. Referring to the equations above, since current changes fast, this could induce quite a bit of uncertainty into the model, but without taking measurement with and LCR meter this is the best we can do in a reasonable amount of time. 

### Calcuation of Mechanical Load Behavior Based on Measured Operating Point
#### Done with Claude - Verified by Cody Kremer
---

Step 1 — Convert the operating point to SI units
$$
T = 2440\ \text{gf} \times 0.00980665\ \frac{\text{N}}{\text{gf}} \approx 23.93\ \text{N} \\
\omega = \frac{2\pi n}{60} = \frac{2\pi (29610)}{60} \approx 3100.8\ \text{rad/s}
$$
Step 2 — Thrust coefficient (quadratic drag form)

$$
T = k_T \omega^2 \quad\Rightarrow\quad k_T = \frac{T}{\omega^2} \\
k_T = \frac{23.93}{(3100.8)^2} \approx 2.49\times10^{-6}\ \frac{\text{N}\cdot\text{s}^2}{\text{rad}^2}
$$

Step 3 — Ideal (Froude/momentum theory) induced power

$$
A = \pi\left(\frac{D}{2}\right)^2, \qquad D = 0.1524\ \text{m} \;\Rightarrow\; A \approx 0.01824\ \text{m}^2 \\
P_{ideal} = \frac{T^{3/2}}{\sqrt{2\rho A}}, \qquad \rho = 1.225\ \frac{\text{kg}}{\text{m}^3} \\
P_{ideal} = \frac{(23.93)^{3/2}}{\sqrt{2(1.225)(0.01824)}} \approx 554\ \text{W}
$$

Step 4 — Actual power, correcting for propeller efficiency

$$
P_{actual} = \frac{P_{ideal}}{FM}, \qquad FM \approx 0.65 \\
P_{actual} = \frac{554}{0.65} \approx 852\ \text{W}
$$

Step 5 — Torque at the operating point

$$
\tau = \frac{P_{actual}}{\omega} = \frac{852}{3100.8} \\\approx 0.275\ \text{N}\cdot\text{m}
$$

Step 6 — Torque (drag) coefficient

$$
\tau = k_Q \omega^2 \quad\Rightarrow\quad k_Q = \frac{\tau}{\omega^2}
k_Q = \frac{0.275}{(3100.8)^2} \approx 2.86\times10^{-8}\ \frac{\text{N}\cdot\text{m}\cdot\text{s}^2}{\text{rad}^2}
$$

Combined closed-form for $k_Q$ (steps 3–6 collapsed into one expression):

$$
k_Q = \frac{T^{3/2}}{FM\sqrt{2\rho A}\,\omega^3}
$$
---