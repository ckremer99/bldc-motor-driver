# Hardware Requirements Specification (HRS)
**Document ID:** BLDC-HRS-001
**Revision:** A
**Author:** Cody Kremer
**Date:** — 26-Aug-2026

## 1. Scope
This project walks though the design process. 

## 2. Applicable Documents
[Any reference standards, datasheets, or parent-system requirements this derives from.]

## 3. Functional Requirements
These requirements will be obtained by assessing the drone specifications. Each motor will contain it's own driver. This means we want the board and controller to be light-weight so the majority of the load can be the payload along with the chassis. We will define these in more detail in this document. 

### Drone Specifications

This drone will be capable of flight at high-altitude (mountainous regions) optimized for battery life and aireal image capturing. The drone should spend most of its time hovering and climbing. We will define the flight characteristics to move upward at a constant rate of 10 m/s. Accelerating up to 2 m/s^2 upward. This requires a maximum thrust to be the drones weight times 2 m/s^2. The 10 m/s constraint reduces the need to consider air resistance from the chassis. 

| Specification | Value |
|---|---|
| Thrust to Weight Ratio | 2:1 |
| Weight | 1 kg | 
| Number of Motors | 4 |
| Thrust Per Moter | 500 g |
| Max Altitude | 10,000 ft. |
| Air Density @ 10000 ft. | 0.001756 slugs/ft³ |
| Flight Time @ Sea-Level  | 25 min |

The altitude constraint suggests the need for a larger propeller size with a lower KV rating. This will put more current demands, which is an important consideration for battery selection. 

We also need to consider reasonable controller specifications. Let's look at some IGBT's considering cost, availability. 

Let's look at Batteries as well using the same design considerations. We also need to account for flight style.

> Battery Pack: 6000 6S Battery Pack

[Battery Information](https://maxamps.com/collections/lipo-5450mah-packs/products/lipo-5450-6s-22-2v-battery-pack?utm_medium=referral&utm_source=unmannedsystemstechnology.com)

> Motor Model: MN501-S

[Motor Datasheet](https://uav-en.tmotor.com/2018/navigato_0402/39.html)


To select the propeller, we want to minimize the output current to make the FET selection less constraining. Based on the propeller selection guide given in the motor datasheet, we find the propeller that minimizes the current draw at 916g of thrust to be 2.87A. The output voltage at this thrust is 24.35 
> Propeller Model: T-MOTOR P22×6.6 Polish Carbon Fiber Drone Propeller

[Propeller Link](https://shop.tmotor.com/products/p22-6-6-carbon-fiber-uav-propeller?srsltid=AfmBOoruno4ZtllN6BsG9sj8xBzgtMtzC_fPKD7mWsG-d3jCablFLd4J)


---



### Driver Specifications
| ID | Requirement | Rationale | Verification Method |
|---|---|---|---|
| REQ-001 | Input voltage range: 16 to 30 VDC | | Draw maximum input current to DC-DC converter then ensure line regulation is less than 5% |
| REQ-002 | Max continuous output current: 3.0 A | | Ensure load regulation is less then 5% |
| REQ-003 | Speed control range: ___ to 3000 RPM | | Ensure efficiency requirement is met at max-rpm |
| REQ-004 | Commutation method: three-step (Reverse EMF) | | Inspection |
| REQ-005 | Speed command interface: SPI | | Assess propeller speed is within 2.5% of speed command  |
| REQ-006 | Overcurrent protection trip threshold: __ A, response time __ | | Test |
| REQ-007 | Undervoltage lockout threshold: 14 V | | Test |
| REQ-008 | Operating temperature range: __ to __ °C | | Thermal camera analysis with driver drawing max steady-state current |

Based on these specifications we can now calculate propeller sizes and motor specifications. 

### Cost Specifications

Since the project is to design driver board for a drone with the following specifications, I will determine a reasonable drone budget with the specifications and allocate a typical driver amount from the specifications derived from the information above. 

| ID | Requirement | Rational |
|---|---|---|

## 4. EMI/EMC Requirements
[Even informal — e.g., "conducted emissions on DC input shall not exceed X per CISPR 25 Class Y" — pick a real standard to practice against.]

## 5. Environmental / Mechanical Requirements
[Board size constraints, connector types, mounting.]

## 6. Safety Requirements
Protections: reverse-polarity; overcurrent

## 7. Traceability
[As you write DVTP test cases later, link each REQ-### to the test case ID that verifies it. Fill this in once 06_Test/DVTP.md exists.]

