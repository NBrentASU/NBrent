---
title: Actuator API
tags:
- tag1
- tag2
---

## Team Definitions

### Team Bytes

| Type |  Byte  |
| -----------| ----------- |
| Start | AZ  |
| Stop | YB |

### Team Addresses

| Name |  Address  |
| -----------| ----------- |
| Noah Brent | N  |
|Evan Skinner| E |
|Kirk Volin| K |
|Hunter Hassebroek| H |
| Broadcast | X |

## Recieved Messages

### Message Type 7 (Start Communication)

|  |  Byte 1     |
| -----------| ----------- |
|Message| StartCommand  |
|Variable Type| uint8_t  |
|Min| 0 |
|Max| 1 |
|Example| 1 (Start)|

### Message Type 15 (Speed Setting from HMI)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Speed Setting  |
|Variable Type| uint8_t  |
|Min|  1 |
|Max|  3 |
|Example| 2 (Medium Speed)|

## Sent Messages

### Message Type 8 (Switchings Per Second)

|  |  Byte 1     |  Byte 2   |
| -----------| ----------- | ----------- |
|Message| # of Switchings | Time Since Last Triggered |
|Variable Type| uint8_t  | uint8_t  |
|Min| 0 | 0 |
|Max| 255 | 100  |
|Example| 12 | 24 (24 milliseconds) |

### Message Type 9 (Error)

|  |  Byte 1     |  Byte 2   |
| -----------| ----------- | ----------- |
|Message| Error Type | Address Received |
|Variable Type| uint8_t  | uint8_t  |
|Min| 0  | Z (No error address) |
|Max| 9 | Address of Error  |
|Example| 2  | E  |

Error Types:

0: Incorrect / No Start Bit
1: Incorrect / No Address Bit
2: Incorrect / No Message Type
3: Incorrect / No Stop Bit
4: Incorrect Data Value in Valid Message
5: Bytes per Message Overflow

### Message Type 10 (Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Reset of Actuator System  |
|Variable Type| uint8_t  |
|Min| 0  |
|Max| 1  |
|Example| 1 (Reset)|

## Code Handling

