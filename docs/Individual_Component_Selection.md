---
title: Individual Component Selection
---

## Component Selection - Actuator Subsystem

#### Microcontroller

### Microcontrollers

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC1.png?raw=true)[PIC18F47Q10 (TQFP/44)](https://www.microchip.com/en-us/product/pic18f47q10)|Pins distributed on 4 sides (more room for traces) / Extra pins should something come up / Same as class DIP| 44 pins (excess of needed) / Difficulty soldering / Extremely small and dense configuration at 10x10x1mm |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC2.png?raw=true)[PIC18F27Q10 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f27q10#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128K Bytes (Flash) / 1k EEPROM | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 31 Deep Hardware Stack / 3.6K SRAM / Confusing documentation regarding pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/PIC3.png?raw=true)[PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)| 7.5x17.9mm / Most pins will be used, minimizing excess soldering / Easier soldering / 128 Deep Hardware Stack / 4K SRAM / Better information for my use case | More pins per side / If a requirement is overlooked now, little to no extra pins to fix it / 64K Bytes (Flash) / 500 EEPROM |

#### Selection

Despite having some downsides memory-wise when compared to the PIC18F27Q10 (SOIC/28), the PIC18F24Q24 (SOIC/28) had the datasheet that best-described functionality regarding our use case which is why the component was selected.

#### Selected PIC Info

| PIC18F24Q24 Info   |  Answer     |
| ------------------ | ----------- |
| Product Page       | [PIC18F24Q24 (SOIC/28)](https://www.microchip.com/en-us/product/pic18f24q24#Documentation)        |
| Datasheet          | [Datasheet](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F24-25Q24-Microcontroller-Data-Sheet-DS40002517.pdf)        |
| Application Notes  | [Application Notes](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ApplicationNotes/ApplicationNotes/AN5226-Getting-Started-PIC18-Q24-Family-DS00005226.pdf)        |
| Vendor             | [Microchip](https://www.microchip.com/)        |
| Examples           | [Examples](https://github.com/eziya/PIC18F_Examples)          |
| External Resources | [External Resources](https://github.com/eziya/PIC18F_Examples)         |
| Unit Cost          | $0.95         |
| Max IC Current     | 250 mA         |
| Max GPIO Current   | 20 mA          |
| Interrupt Support  | Yes         |
| Requirements       | [Requirements (On Datasheet)](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F24-25Q24-Microcontroller-Data-Sheet-DS40002517.pdf)                  |
| MPLabX Support     | Yes         |
| MCC Support        | Yes           |

#### Necessary Pins

| Module         | # Available | Needed | Associated Pins |
| -------------- | ----------- | ------ | ------------------------------ |
| UART           |  2           | 2      |GPIO43 ~ GPIO44, GPIO17 ~ GPIO18|
| External SPI   |  3           | 3      | SDI, SDO, SCK                            |
| I2C            |  2           | 0      | SDA, SDL                           |
| GPIO           |  2           | 2      | *                              |
| ADC            |  19           | 0      | ADC                           |
| PWM            |  3           | 0      | *                              |
| ICSP           |  3          | 3      | MOSI, MISO, SCK                         |

#### MPLabX (No Error & MCC / Melody Support)

![](https://github.com/NBrentASU/NBrent/blob/main/PICNoErrMCC.PNG?raw=true)

PIC loaded in MCC with no errors.

### On-Board Switching Voltage Regulator

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/SVR1.jpg?raw=true)[REG102UA-3.3](https://www.digikey.com/en/products/detail/rochester-electronics,-llc/REG102UA-3.3/13484871?gclsrc=aw.ds&&utm_adgroup=Integrated%20Circuits%20%28ICs%29&utm_source=google&utm_medium=cpc&utm_campaign=Shopping_DK%2BSupplier_Rochester&utm_term=&utm_content=Integrated%20Circuits%20%28ICs%29&utm_id=go_cmp-14247218536_adg-128566365520_ad-539599078936_pla-354083419805_dev-c_ext-_prd-13484871_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ7S7nYkK_YB7_vSCh4ywOoDLnH9ICCjoFQEwViat1UD6Vfm8szarw0aArS0EALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ7S7nYkK_YB7_vSCh4ywOoDLnH9ICCjoFQEwViat1UD6Vfm8szarw0aArS0EALw_wcB&gclsrc=aw.ds)| Cost-effective / Simple wiring, fixed output | Limiting input voltage at 10V / Outputs only 250 mA / Has lead times, bulk quantity only / 0.15x0.19in, small but only 8 pins |
|![](https://github.com/NBrentASU/NBrent/blob/main/SV2.jpg?raw=true)[LM2674MX-3.3/NOPB](https://www.digikey.com/en/products/detail/texas-instruments/LM2674MX-3-3-NOPB/366902)| 500 mA output / Fixed voltage output of 3.3V / 5x3.9mm, slightly larger than other option with same pins / 6.5-40V input / Essentially same as in class regulator | If the voltage to the board ever needed to change (unlikely), this is not adjustable |
|![](https://github.com/NBrentASU/NBrent/blob/main/SV3.jpg?raw=true)[TLV61048DBVR](https://www.digikey.com/en/products/detail/texas-instruments/TLV61048DBVR/10715594)| Cheapest option at $0.63 / 3.7A output / 3-14V adjustable output / Only 6 pins | Only 2.65-5.5V input / 1.75x1.9mm / extremely small |

#### Selection

Due to the voltage more than likely not needing to change from 3.3V, the best option would be the LM267 as it provides enough amperage at 3.3V to power my board. Its size is a bit small but only 6 of the pins need soldering and it will be achievable. The flexibility of the input voltage allows the power to change if needed and still be able to handle regulating the board power.

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
|![](https://github.com/NBrentASU/NBrent/blob/main/ElMag1.jpg?raw=true)[5V Electromagnet - 5 Kg Holding Force](https://www.digikey.com/en/products/detail/adafruit-industries-llc/3873/9603612?gclsrc=aw.ds&&utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Medium%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20223376311_adg-_ad-__dev-c_ext-_prd-9603612_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ5WKWw-robt78EKtD-B8f81DkdjWdAIubvTPCu8aymObWYqTjOJ2UEaAlbREALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ5WKWw-robt78EKtD-B8f81DkdjWdAIubvTPCu8aymObWYqTjOJ2UEaAlbREALw_wcB&gclsrc=aw.ds)| Premade, comes with documented voltages and amperages / Simple design, compact | Would either need a hole drilled through or be fixtured above / Non-flexible (no “real” adjustment if too weak or strong) / $10 per magnet / 5 kg holding force |
|![](https://github.com/NBrentASU/NBrent/blob/main/ElMag2.PNG?raw=true)[Adafruit Industries 3875 Magnets](https://www.jameco.com/z/3875-Adafruit-Industries-5V-Electromagnet-25-Kg-Holding-Force-P40-20_2515575.html)| 25kg holding force (not same as pulling force) / Premade, comes with documented voltages and amperages | $23 per magnet / Would either need a hole drilled through or be fixtured above / Non-flexible (no “real” adjustment if too weak or strong) |
|![](https://github.com/NBrentASU/NBrent/blob/main/ElMag3.jfif?raw=true)Homemade Electromagnet: Hand wound with 30 AWG magnet wire around a hollow core (most likely 3D printed)| Adjustable to specific needs or issues / Around 10 bucks for a quarter pound of material / Can be remade if something happens | Excess calculations and research needed / Making CAD files for hollow core / Potential heating issues |

#### Selection

The homemade magnet will be best for the actuator subsystem due to its use case. During component research, anything high power was out of budget and did not have a “through hole” for a marble to accelerate through. Buying and assembling the magnets from scratch allows for a high level of control over input voltage and amperage to adjust the Gauss strength.

### Magnet Driver Component

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/MD1.jpg?raw=true)[DRV8830](https://www.digikey.com/en/products/detail/texas-instruments/DRV8830DGQR/2520907?gclsrc=aw.ds&&utm_adgroup=Texas%20Instruments&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Supplier_Texas%20Instruments&utm_term=&utm_content=Texas%20Instruments&utm_id=go_cmp-17816159938_adg-_ad-__dev-c_ext-_prd-2520907_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ5tKujN_BY54lgqb8AoSnSqYO7bPmppr_dBQ7gctZH5s2T3429YGnIaAuWuEALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ5tKujN_BY54lgqb8AoSnSqYO7bPmppr_dBQ7gctZH5s2T3429YGnIaAuWuEALw_wcB&gclsrc=aw.ds)| Runs off of 3.3V like the rest of the system / $2.09 per chip | Max output of 6.8V at 1 A (May not be enough) / Only can drive one coil (would need 2) / 3x3mm, small for soldering |
|![](https://github.com/NBrentASU/NBrent/blob/main/MD2.jpg?raw=true)[DRV10983QPWPRQ1](https://www.digikey.com/en/products/detail/texas-instruments/DRV10983QPWPRQ1/7400092)| Max Output of 28V at 2A / 7.8x6.4mm, decent size but is 24 pins / Built-in buck converter / Built-in over-current protection | Would require a voltage regulator of 6.2V+ / $4.09 per chip / Fairly overbuilt for what is needed / For 3 phase motor (it seems) |
|![](https://github.com/NBrentASU/NBrent/blob/main/MD3.jpg?raw=true)[NCV7703CD2R2G](https://www.digikey.com/en/products/detail/onsemi/NCV7703CD2R2G/7325621)| 8.55x5.8mm, good size for 14 pins / 1 A output per pin at 5.5-40V / Takes same voltage as the rest of the board | Has 3 Outputs, can be solved with a logic gate |

#### Selection

The NCV chip is the best overall option due to its SPI support, the wide output range of voltages and amperages, wide pin spacings, and taking the same 3.3V as the microcontroller (as logic power only). There are two downsides however, the first of which is the 16-bit serial buses of this driver communicating with the 8-bit microcontroller. This will take extra coding but should work due to my microcontroller having selectable frequencies up to 64 MHZ and the driver having 5 MHZ. This means that the microcontroller can send 2 8-bit strings to the driver so that it will register as a single 16-bit string and the driver’s sending a 16-bit string being able to be broken and stored into 2 8-bit strings for interpretation on chip. The second of which is this chip has 3 outputs instead of an even 4 to handle both magnets. This is easily solvable by either using 2 of these chips or integrating a logic circuit to switch between magnets.

### Power Input

| Components         |  Pros       |  Cons       |
| ------------------ | ----------- | ----------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/PI1.jpg?raw=true)[PJ-102AH](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices-/PJ-102AH/408448?gclsrc=aw.ds&&utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_Connectors%2C%20Interconnects&utm_term=&utm_content=&utm_id=go_cmp-20461032180_adg-_ad-__dev-c_ext-_prd-408448_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ4MZP29gkNgu7pEoUSMZFq5I9cTc-L2KfLwFuuW4zQ1mDTi0FILMmYaAiuXEALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ4MZP29gkNgu7pEoUSMZFq5I9cTc-L2KfLwFuuW4zQ1mDTi0FILMmYaAiuXEALw_wcB&gclsrc=aw.ds)| 5A rated / Simple 3 prong / $0.76 per jack / 24 VDC | Not technically surface mount, can be altered to be |
|![](https://github.com/NBrentASU/NBrent/blob/main/PI2.jpg?raw=true)[PJ-002B](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-002B/96965)| 2.5A rated / Simple 3 prong / $0.49 per jack / 24 VDC | Not technically surface mount, can be altered to be |
|![](https://github.com/NBrentASU/NBrent/blob/main/PI3.jpg?raw=true)[54-00127](https://www.digikey.com/en/products/detail/tensility-international-corp/54-00127/9685436)| 6A rated / 48 V Input / $0.61 per jack / Simple 3 prong / Non-standard casing, either pro or con | Not technically surface mount, can be altered to be |

#### Selection

Most barrel jacks at this level come down to personal preference as my maximum expected load is lower than most of the barrel’s minimum ratings. Given this the PJ-102AH will be used. Even though it is slightly more expensive it gives a bit more headway at 5A rather than 2.5A while looking standard.

### Non-Critical, Debugging Components

#### Button

| Components         |  Purpose       |
| ------------------ | -------------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/Button1.jfif?raw=true)Button| Simple, non-descript button for sending 3.3V to GPIO pin for debugging and/or proving UART connection between boards over a daisy chain |


#### LED

| Components         |  Purpose       |
| ------------------ | -------------- |
|![](https://github.com/NBrentASU/NBrent/blob/main/LED1.jpg?raw=true)LED| Simple 2-legged LED (will alter for surface mounting) to show debugging status, prove UART connection between boards over daisy chain, and potentially the electromagnet switching status. |
