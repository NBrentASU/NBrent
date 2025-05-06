---
title: Actuator Block Diagram
tags:
- tag1
- tag2
---

## Subsystem: Actuator

![Block Diagram](https://github.com/NBrentASU/NBrent/blob/main/Block%20Diagram-314-Noah.drawio.png?raw=true)

Link to [Actuator Block Diagram](https://drive.google.com/file/d/1WcJ86UYoO9e4S2_K3oaGFfPS9JR9rR2P/view?usp=sharing)

Above is the Actuation Subsystem for Team 310 created by Noah Brent. This achieves actuation via data sent from the sensor subsystem which turns on or off the electromagnets. Depending on the data recieved, an SPI motor driver chip will send current into the electromagnet to pull and push the steel ball by switching the current and changing the magnetic field. Data regarding these switchings and timings will then be sent to the MQTT and HMI subsystems for recording and displaying respectively.

This block diagram fulfills the needs of our project by providing visual representations of our concept, electromagnetism. Our team opted for an accelerator as young kids are often drawn to exciting or magical things. Our actuator fits this description as there is no physical forces keeping the ball in motion except for our invisible magnetic fields. 