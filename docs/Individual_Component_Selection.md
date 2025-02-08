---
title: Individual Component Selection
---

## Component Selection - Actuator Subsystem

#### Microcontroller

#### Pin Requirements

| Module         | # Available | Needed | Associated Pins (or * for any) |
| -------------- | ----------- | ------ | ------------------------------ |
| UART           |             | 2      |GPIO43 ~ GPIO44, GPIO17 ~ GPIO18|
| External SPI   |             | 3      | N/A                            |
| I2C            |             | 0      | N/A                            |
| GPIO           |             | 2      | *                              |
| ADC            |             | 0      | N/A                            |
| PWM            |             | 0      | *                              |
| ICSP           |             | 3      | N/A                            |

### Microcontrollers

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC1.png?raw=true)[PIC18F47Q10 (TQFP/44)](https://www.microchip.com/en-us/product/pic18f47q10)|Pins distributed on 4 sides (more room for traces) / Extra pins should something come up / Same as class DIP| 44 pins (excess of needed) / Difficulty soldering / Extremely small and dense configuration at 10x10x1mm |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC2.png?raw=true)[PIC18F27Q10 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f27q10#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128K Bytes (Flash) / 1k EEPROM | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 31 Deep Hardware Stack / 3.6K SRAM / Confusing documentation regarding pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC3.png?raw=true)[PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128 Deep Hardware Stack / 4K SRAM / Better information for my use case | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 64K Bytes (Flash) / 500 EEPROM |

#### Selection

Despite having some downsides memory-wise when compared to the PIC18F27Q10 (SOIC/28), the PIC18F24Q24 (SOIC/28) had the datasheet that best-described functionality regarding our use case which is why the component was selected.

### Selected PIC Info

| PIC18F24Q24 Info   |  Answer     |
| ------------------ | ----------- |
| Product Page       | Link        |
| Datasheet          | Link        |
| Application Notes  | Link        |
| Vendor             | Digikey     |
| Examples           | 2           |
| External Resources | 45          |
| Unit Cost          | 2           |
| Max IC Current     | 5           |
| Max GPIO Current   | 0           |
| Interrupt Support  | 1           |
| Requirements       | 5           |
| MPLabX Support     | 0           |
| MCC Support        | 1           |

### On-Board Switching Voltage Regulator

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### Selection



### Electromagnet Switching Voltage Regulator 

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### Selection

The LM2594M is the best option for my electromagnet’s power needs. The wide range of voltage adjustability on the inputs and outputs allows for it to be tweaked as needed to use the full power of the designed magnet. The extra room for experimentation will allow for the best outcome possible.

### Electromagnets

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### Selection


### Magnet Driver Component

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### Selection


### Power Input

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### Selection


### Non-Critical, Debugging Components

#### Button

| Components         |  Pros       |  Cons       |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |

#### LED

| Components         |  Pros       |  Cons       |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |
|                    |             |             |