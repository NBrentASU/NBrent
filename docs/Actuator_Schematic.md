---
title: Schematic
tags:
- tag1
- tag2
---

## Schematic

![](https://github.com/NBrentASU/NBrent/blob/main/SchematicPNG.png?raw=true)

[Link to Actuator Schematic PDF]()

[Link to Actuator Schematic Altium File](https://github.com/NBrentASU/NBrent/blob/main/Individual_Subsystem%20(2-26-2025%208-36-59%20AM).zip)

Above is the schematic of the actuator subsystem in Altium. The PIC microcontroller is a custom-made symbol due to importing issues, all other components come from Digikey or the built-in manufacturer part search. Altium was chosen as the platform due to its online-sharing capabilities as well as the built-in library. 

There are 4 main sections of the subsystem to accomplish its functions.

The power regulators and power inputs are located in the top left. This section allows for power inputs via the daisy chain set up or on-board power jack. The upper regulator is for any 3.3V requirements such as logic power, microcontroller, LEDs, etc. The lower regulator is exclusively to power the electromagnets, starting with 9V and 1.5A. This is an adjustable regulator as to be able to fine-tune the required voltage and amperage to effectively pull the steel marble. These voltages are then routed to their VDD and VS paths respectively.

The connectors section contains the programming and daisy chain connections. The Snap programmer provided by the professors requires 5 pins (MCLR, VDD, GND, DAT, CLK) in order to properly interface with the provided PIC. Using a set of 5 headers allows for easy programming through paths to their respective ICSP pins. The 2x4 molex connector is the daisy chain which facilitates board-to-board communication and eventual power transfer. Pins 1-5 and 8 will be used to send and recieve information to control and document the electromagnetic switchings.

The microcontroller section contains all of the necessary hardware to operate, debug, and program the PIC microcontroller. This includes the MCLR programming circuit, ICSP programming pins, debugging LEDS, pushbutton for testing, UART messaging pins, and SPI interfacing with electromagnets.

The electromagnet section contains 2 electromagnets with bi-directional EMF flyback diodes, each with an SPI driver communicating with the PIC. This system allows a reduced SPI pin requirement as each chip can be activated from their CSB pin. From there, serial data will be sent to determine current flow which will affect the direction of the magnetic flow to push or pull the marble. These SPI drivers are 16 bit whereas the PIC is only 8-bit. However, the PIC has an operational range of 64 MHz where the chips operate at 5 MHz meaning 2 8-bit messages can be sent at 10 MHz to mimic a 5 MHz 16-bit signal.