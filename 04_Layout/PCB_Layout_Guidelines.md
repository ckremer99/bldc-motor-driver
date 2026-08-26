# PCB Layout Guidelines
**Document ID:** BLDC-LAY-001

*Written as if handing this to a separate layout designer — even though you'll execute it yourself. This is the practice: learn to specify layout intent precisely.*

## 1. Stackup
[Layer count, copper weight for power layers, why.]

## 2. Critical Placement Constraints
[Gate driver proximity to MOSFET gates, bootstrap cap placement, current sense shunt Kelvin connections, decoupling cap placement.]

## 3. High-Current Path Requirements
[Trace width/copper pour sizing for phase currents and DC bus, via stitching.]

## 4. EMI/Grounding Requirements
[Ground pour strategy, return path for switching currents, CM choke placement relative to connector, keep-out around Hall sensor lines from switching nodes.]

## 5. Thermal Requirements
[Copper area/thermal vias under MOSFETs per the thermal analysis.]

## 6. What I Actually Did (post-layout notes)
[After you lay it out yourself, note where you deviated from these guidelines and why — that gap is often the most honest engineering learning.]
