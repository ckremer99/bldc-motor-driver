
# Model Devlopment of Power Converter

## Power Schema

12V ---> 48V ---> 30V Variable Powersupply ---> BLDC Motor Driver

12V ---> 5V ---> uC

We will be modeling the main power system to ensure it can meet the needs of the specifications and we can determine the necessary component values to create the schematic. Below shows the basic boost converter layout. 

![Boost Converter](Images/Design_Overview/Basic_Boost_Converter_Schematic.jpeg)

The boost converter system has an input voltage and an output voltage. We will derive the equations needed to model the system. 

The switch current is not continuous so for our first block this will not be the output. The current across the inductor however will be continuous, but the equations governing it change based on the state of the system. 

When the switch is open, the governing equation for the system becomes 