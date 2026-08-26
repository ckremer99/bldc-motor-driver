# Hardware Requirements Specification (HRS)
**Document ID:** BLDC-HRS-001
**Revision:** A
**Author:** Cody Kremer
**Date:** — 26-Aug-2026

## 1. Scope
[What this board is, what system it's part of (hypothetical or real), what it is NOT responsible for.]

## 2. Applicable Documents
[Any reference standards, datasheets, or parent-system requirements this derives from.]

## 3. Functional Requirements
These requirements will be obtained by assessing the drone specifications. Each motor will contain it's own driver. This means we want the board and controller to be light-weight so the majority of the load can be the payload along with the chassis. We will define these in more detail in this document. 

### Drone Specifications
Drone Performance Specifications 
| Specification | Value |
|---|---|
| Thrust to Weight Ratio | 2:1 |
| Weight | 1 kg | 
| Number of Motors | 4 |
| Thrust Per Moter | 500 g |
| Max Altitude | 10,000 ft. |
| Air Density @ 10000 ft. | 0.001756 slugs/ft³ |

---

### Driver Specifications
| ID | Requirement | Rationale | Verification Method |
|---|---|---|---|
| REQ-001 | Input voltage range: __ to __ VDC | | Test |
| REQ-002 | Max continuous output current: __ A | | Test/Analysis |
| REQ-003 | Speed control range: __ to __ RPM | | Test |
| REQ-004 | Commutation method: sensored six-step (Hall) | | Inspection |
| REQ-005 | Speed command interface: __ (PWM / analog / digital) | | Test |
| REQ-006 | Overcurrent protection trip threshold: __ A, response time __ | | Test |
| REQ-007 | Undervoltage lockout threshold: __ V | | Test |
| REQ-008 | Operating temperature range: __ to __ °C | | Analysis |

Based on these specifications we can now calculate propeller sizes and motor specifications. 

### Cost Specifications
| ID | Requirement | Rational |
|---|---|---|

## 4. EMI/EMC Requirements
[Even informal — e.g., "conducted emissions on DC input shall not exceed X per CISPR 25 Class Y" — pick a real standard to practice against.]

## 5. Environmental / Mechanical Requirements
[Board size constraints, connector types, mounting.]

## 6. Safety Requirements
[Protections: reverse polarity, overcurrent, overtemperature, etc.]

## 7. Traceability
[As you write DVTP test cases later, link each REQ-### to the test case ID that verifies it. Fill this in once 06_Test/DVTP.md exists.]

