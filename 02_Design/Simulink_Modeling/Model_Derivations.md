

# Model Derivations

The objective of the simulink model is to determine the behavior of the drone acceleration in terms of the electrical inputs. 

## Equations Governing BLDC Motor Behavior

![bldc motor mechanical model](images/electromechanical_model_of_motor.png)

$$
u_a = R • i_a + L\frac{di_a}{dt} + e_a \\[1.5ex]
u_b = R • i_b + L\frac{di_b}{dt} + e_b \\[1.5ex]
u_c = R • i_c + L\frac{di_c}{dt} + e_c
$$

These equations show the voltage at the stator winding accounting for the resistive losses of the coil, the stator inductance, and the back-emf. 

$$
\begin{align}
e_A &= K_w • f(θ_e) \,•\, ω \\
e_B &= K_w • f(θ_e - \frac{2π}{3})\,•\, ω \\
e_C &= K_w • f(θ_e + \frac{2π}{3})\,•\,ω
\end{align}
$$

### Mechanical Equations

$$
T_{total}=T_{load}+J\,•\frac{dω}{dt} + b\,•\,ω
$$

### Parameters Needed

|Parameter Name|Symbol|Unit|
|---|---|---|
|Winding Resistance|$R$|$\Omega$|
|Winding Inductance|$L$|$H$|
|Pole Pairs|$K_w$|constant|
|Rotor Inertia|$J$|$\text{kg}/m^2$

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
