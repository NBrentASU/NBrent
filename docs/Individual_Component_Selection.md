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
|![](https://github.com/NBrentASU/NBrent/blob/main/SVR1.jpg?raw=true)[REG102UA-3.3](https://www.digikey.com/en/products/detail/rochester-electronics,-llc/REG102UA-3.3/13484871?gclsrc=aw.ds&&utm_adgroup=Integrated%20Circuits%20%28ICs%29&utm_source=google&utm_medium=cpc&utm_campaign=Shopping_DK%2BSupplier_Rochester&utm_term=&utm_content=Integrated%20Circuits%20%28ICs%29&utm_id=go_cmp-14247218536_adg-128566365520_ad-539599078936_pla-354083419805_dev-c_ext-_prd-13484871_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ7S7nYkK_YB7_vSCh4ywOoDLnH9ICCjoFQEwViat1UD6Vfm8szarw0aArS0EALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ7S7nYkK_YB7_vSCh4ywOoDLnH9ICCjoFQEwViat1UD6Vfm8szarw0aArS0EALw_wcB&gclsrc=aw.ds)| Cost-effective / Simple wiring, fixed output | Limiting input voltage at 10V / Outputs only 250 mA / Has lead times, bulk quantity only / 0.15x0.19in, small but only 8 pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/SV2.jpg?raw=true)[LM2674MX-3.3/NOPB](https://www.digikey.com/en/products/detail/texas-instruments/LM2674MX-3-3-NOPB/366902)| 500 mA output / Fixed voltage output of 3.3V / 5x3.9mm, slightly larger than other option with same pins / 6.5-40V input / Essentially same as in class regulator | If the voltage to the board ever needed to change (unlikely), this is not adjustable |
|![](https://github.com/NBrentASU/NBrent/blob/main/SV3.jpg?raw=true)[TLV61048DBVR](https://www.digikey.com/en/products/detail/texas-instruments/TLV61048DBVR/10715594)| Cheapest option at $0.63 / 3.7A output / 3-14V adjustable output / Only 6 pins | Only 2.65-5.5V input / 1.75x1.9mm / extremely small |

#### Selection



### Electromagnet Switching Voltage Regulator 

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/MV1.jpg?raw=true)[TPS562201DDCR](https://www.digikey.com/en/products/detail/texas-instruments/TPS562201DDCR/5808210)| Adjustable switching / 2A current / Similar to class regulator / Wide input range, 4.5-17V / Low cost of $0.35 | Max voltage is 7V which is lower than would be comfortable with / 3x1.75mm, pretty small |
|![](https://github.com/NBrentASU/NBrent/blob/main/MV2.jpg?raw=true)[LM2594M-12](https://www.digikey.com/en/products/detail/umw/LM2594M-12/16705976)| 5x4mm, good size / 3A output, more than required / Wide output voltage | Costly at $3.72 per chip |
|![](https://github.com/NBrentASU/NBrent/blob/main/MV3.jpg?raw=true)[LM2594M-ADJ](https://www.digikey.com/en/products/detail/umw/LM2594M-ADJ/16705956?s=N4IgjCBcoCwdIDGUBmBDANgZwKYBoQB7KAbRAGYwAGcgdgCYQBdAgBwBcoQBldgJwCWAOwDmIAL4EAtDCihkkdNnwgAbkNSZcBYpDLUArDFpVmbTpBATx4oA)| Decently priced for performance at $2.68 per chip / 1.5A, exactly what is needed / Wide input voltage of 4.5-40V / Wide output voltages of 1.23-37V | Extra framework needed to set voltage |

#### Selection

The LM2594M is the best option for my electromagnet’s power needs. The wide range of voltage adjustability on the inputs and outputs allows for it to be tweaked as needed to use the full power of the designed magnet. The extra room for experimentation will allow for the best outcome possible.

### Electromagnets

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC1.png?raw=true)[PIC18F47Q10 (TQFP/44)](https://www.microchip.com/en-us/product/pic18f47q10)|Pins distributed on 4 sides (more room for traces) / Extra pins should something come up / Same as class DIP| 44 pins (excess of needed) / Difficulty soldering / Extremely small and dense configuration at 10x10x1mm |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC2.png?raw=true)[PIC18F27Q10 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f27q10#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128K Bytes (Flash) / 1k EEPROM | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 31 Deep Hardware Stack / 3.6K SRAM / Confusing documentation regarding pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC3.png?raw=true)[PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128 Deep Hardware Stack / 4K SRAM / Better information for my use case | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 64K Bytes (Flash) / 500 EEPROM |

#### Selection


### Magnet Driver Component

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC1.png?raw=true)[PIC18F47Q10 (TQFP/44)](https://www.microchip.com/en-us/product/pic18f47q10)|Pins distributed on 4 sides (more room for traces) / Extra pins should something come up / Same as class DIP| 44 pins (excess of needed) / Difficulty soldering / Extremely small and dense configuration at 10x10x1mm |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC2.png?raw=true)[PIC18F27Q10 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f27q10#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128K Bytes (Flash) / 1k EEPROM | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 31 Deep Hardware Stack / 3.6K SRAM / Confusing documentation regarding pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC3.png?raw=true)[PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128 Deep Hardware Stack / 4K SRAM / Better information for my use case | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 64K Bytes (Flash) / 500 EEPROM |

#### Selection


### Power Input

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC1.png?raw=true)[PIC18F47Q10 (TQFP/44)](https://www.microchip.com/en-us/product/pic18f47q10)|Pins distributed on 4 sides (more room for traces) / Extra pins should something come up / Same as class DIP| 44 pins (excess of needed) / Difficulty soldering / Extremely small and dense configuration at 10x10x1mm |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC2.png?raw=true)[PIC18F27Q10 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f27q10#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128K Bytes (Flash) / 1k EEPROM | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 31 Deep Hardware Stack / 3.6K SRAM / Confusing documentation regarding pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC3.png?raw=true)[PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128 Deep Hardware Stack / 4K SRAM / Better information for my use case | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 64K Bytes (Flash) / 500 EEPROM |

#### Selection


### Non-Critical, Debugging Components

#### Button

| Components         |  Purpose       |
| ------------------ | -------------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/Button1.jfif?raw=true)Button| Simple, non-descript button for sending 3.3V to GPIO pin for debugging and/or proving UART connection between boards over a daisy chain |


#### LED

| Components         |  Purpose       |
| ------------------ | -------------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/LED1.jpg?raw=true)LED| Simple 2-legged LED (will alter for surface mounting) to show debugging status, prove UART connection between boards over daisy chain, and potentially the electromagnet switching status. |
