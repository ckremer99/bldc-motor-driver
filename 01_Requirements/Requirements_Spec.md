# Hardware Requirements Specification (HRS)
**Document ID:** BLDC-HRS-001
**Revision:** A
**Author:** Cody Kremer
**Date:** —

## 1. Scope
[What this board is, what system it's part of (hypothetical or real), what it is NOT responsible for.]

## 2. Applicable Documents
[Any reference standards, datasheets, or parent-system requirements this derives from.]

## 3. Functional Requirements
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

## 4. EMI/EMC Requirements
[Even informal — e.g., "conducted emissions on DC input shall not exceed X per CISPR 25 Class Y" — pick a real standard to practice against.]

## 5. Environmental / Mechanical Requirements
[Board size constraints, connector types, mounting.]

## 6. Safety Requirements
[Protections: reverse polarity, overcurrent, overtemperature, etc.]

## 7. Traceability
[As you write DVTP test cases later, link each REQ-### to the test case ID that verifies it. Fill this in once 06_Test/DVTP.md exists.]

---
*Fill-in guidance: each requirement should be a single, testable, unambiguous statement — avoid "should" (use "shall"), avoid vague terms like "adequate" or "sufficient." If you can't write a verification method for a requirement, it's not specific enough yet.*
