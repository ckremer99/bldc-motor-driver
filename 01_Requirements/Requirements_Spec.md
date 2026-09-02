# Hardware Requirements Specification (HRS)
**Document ID:** BLDC-HRS-001
**Revision:** A
**Author:** Cody Kremer
**Date:** — 26-Aug-2026

## 1. Scope
This project walks though the design process of a drone-driver system. The scope of the requirments includes specifications for drone performance to provide a realistic view of what requirements would be given in an engineering setting. 

Although there are many more components to the drone system the project focuses on the driver board hence we will focus on the requirements of the driver rather than getting bogged down in the details. More depth would be added with a wider time-frame. 

## 2. Functional Requirements
These requirements will be obtained by assessing the drone specifications. Each motor will contain it's own driver. This means we want the board and controller to be light-weight so the majority of the load can be the payload along with the chassis. We will define these in more detail in this document. 

### Drone Specifications

This drone will be capable of flight at high-altitude (mountainous regions) optimized for battery life and aireal image capturing. The drone should spend most of its time hovering and climbing. We will define the flight characteristics to move upward at a constant rate of 10 m/s. Accelerating up to 2 $m/sec^2$ upward. This requires a maximum thrust to be the drones weight times 2 m/s^2. The 10 m/s constraint reduces the need to consider air resistance from the chassis. 

| Specification | Value |
|---|---|
| Thrust to Weight Ratio | 2:1 |
| Weight | 2.5 kg | 
| Number of Motors | 4 |
| Max Altitude | 10,000 ft. |
| Flight Time @ Sea-Level  | 25 min |

Note: Changed weight spec from 1 kg to 2.5 kg 
- Justification: Supports heavier payload and makes project more interesting. 


## 3. Basic Product Selection

This section ensures realistic design decisions could be made using real parts that are currently in the market. 

The motors together draw 40A around hovering thrust. If we want a 25 min flight time we need batteries that together supply ~16000 mA battery. 

We need 3 of the following battery pack. The battery driver is beyond the scope of this project however the weight of the 3 packs is around 1.8 kg: 

> Battery Pack: 6000 6S Battery Pack

[Battery Information](https://maxamps.com/collections/lipo-5450mah-packs/products/lipo-5450-6s-22-2v-battery-pack?utm_medium=referral&utm_source=unmannedsystemstechnology.com)


The motor chosen supports the thrust requirements of the system and its characteristics are given in a table on the website. 

> Motor Model: MN501-S

[Motor Datasheet](https://uav-en.tmotor.com/2018/navigato_0402/39.html)


To select the propeller, we want to minimize the output current to make the FET selection less constraining. Based on the propeller selection guide given in the motor datasheet, we find the propeller that minimizes the current draw at 916g of thrust to be 2.87A. The output voltage at this thrust is 24.35 
> Propeller Model: T-MOTOR P22×6.6 Polish Carbon Fiber Drone Propeller

[Propeller Link](https://shop.tmotor.com/products/p22-6-6-carbon-fiber-uav-propeller?srsltid=AfmBOoruno4ZtllN6BsG9sj8xBzgtMtzC_fPKD7mWsG-d3jCablFLd4J)


---

Refer to [Calculations and Analysis](Calculations_and_Analysis.md) for derivations. 

### Driver Specifications
| ID | Requirement | Rationale | Verification Method |
|---|---|---|---|
| REQ-001 | Input voltage range: 16 to 30 VDC | Refer to calculations| Draw maximum input current to DC-DC converter then ensure line regulation is less than 5% |
| REQ-002 | Max continuous output current: 55 A | Refer to calculations | Ensure load regulation is less then 5% |
| REQ-003 | Speed control range: 11,000 to 30,000 RPM | Range of table. | Ensure efficiency requirement is met at max-rpm |
| REQ-004 | Commutation method: six-step (Reverse EMF) | No hall-effect sensor in motor| Tach measurement to obtain error |
| REQ-005 | Speed command interface: SPI | Not many slave devices and most reliable. Simplest | Assess propeller speed is within 2.5% of speed command  |
| REQ-006 | Overcurrent protection trip threshold: 60 A, response time 100 us | Temp can't increase dramatically in that timeframe | short circuit using switch and measure time between events using uC to read fault flag |
| REQ-007 | Undervoltage lockout threshold: 14 V | Places strain on boost converter at that voltage | Digital power supply adjustments |
| REQ-008 | Operating temperature range: -20 to 175 °C | Handles temps at altitude along with max switch ratings | Thermal camera analysis with driver drawing max steady-state current |



