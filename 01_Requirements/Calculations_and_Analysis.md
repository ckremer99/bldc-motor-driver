
# Calculations and Analysis

In this section, we examine the order in which we collect our data to obtain the necessary specifications of our system. Let's review the constraints of our drone as a starting point. 

## Drone Specifications

| Specification | Value |
|---|---|
| Thrust to Weight Ratio | 2:1 |
| Weight | 2.5 kg | 
| Number of Motors | 4 |
| Max Altitude | 10,000 ft. |
| Flight Time @ Sea-Level  | 25 min |


## Motor Selection 

### Navigator MN501-S Motor Highlights
- Available in KV240, KV300, and KV360 configurations
- Designed for professional multirotor UAV applications
- Up to 5.2kg maximum thrust
- IP45-rated dust-resistant and anti-corrosion construction
- Centrifugal cooling design for efficient heat dissipation
- High-temperature-resistant magnets, stator, and windings
- Precision dynamic balancing for smooth and stable operation

The altitude constraint suggests the need for a larger propeller size with a lower KV rating. I'll look into the KV240 Model. 

### Important Motor Specs: 
![Motor Specs Image](images/motor_specs.png)

Weight of 4 motor modules: 1400g
Weight Remaining: 2500g - 1400g = 1600g

We also need to consider reasonable controller specifications. Let's look at some IGBT's considering cost, availability. 

#### IXSJ Series SiC MOSFETs

Vds(max): 1200V 
Condtinuous Ids(max): 28A-85A
Drive Voltage: 18V (That's kinda a lot)


Let's look at Batteries as well using the same design considerations. We also need to account for flight style.