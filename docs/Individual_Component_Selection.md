---
title: Individual Component Selection
---

## Component Selection - Actuator Subsystem

### On-Board Switching Voltage Regulator



#### Selection

Despite having some downsides memory-wise when compared to the PIC18F27Q10 (SOIC/28), the PIC18F24Q24 (SOIC/28) had the datasheet that best-described functionality regarding our use case which is why the component was selected.

### Power Input



#### Selection

For powering this subsystem, I feel that versatility is important. Because USB is already required to program the ESP32 chip, I will design the circuit board so that it can be powered from either the USB connector or a separate 5.5x2.5mm barrel jack which is a common standard that my teammates and I already have cables for through the Robotics 1 and 2 courses through the Robotics 1 and 2 courses.

### PIC



#### Pin Requirements

| Module         | # Available | Needed | Associated Pins (or * for any) |
| -------------- | ----------- | ------ | ------------------------------ |
| Power          | 2           | 2      | 3V3, EN                        |
| Ground         | 2           | 2      | GND, GND                       |
| UART           | 3           | 2      |GPIO43 ~ GPIO44, GPIO17 ~ GPIO18|
| External SPI   | 4           | 0      | N/A                            |
| I2C            | 2           | 0      | N/A                            |
| GPIO           | 45          | 3      | *                              |
| ADC            | 2           | 0      | N/A                            |
| LED PWM        | 5           | 5      | *                              |
| Motor PWM      | 0           | 0      | N/A                            |
| USB Programmer | 1           | 1      | GPIO19 ~ GPIO20                |
