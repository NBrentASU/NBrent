---
title: Actuator API
tags:
- tag1
- tag2
---

## Recieved Messages

### Message Type 7 (Start Communication)

|  |  Byte 1     |
| -----------| ----------- |
|Message| StartCommand  |
|Variable Type| uint8_t  |
|Min| 0 |
|Max| 1 |
|Example| 1 |

### Message Type 15 (Send Speed Setting)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Speed Setting  |
|Variable Type| uint8_t  |
|Min|  1 | 
|Max|  3 |
|Example|  2 |

## Sent Messages

### Message Type 8 (Magnet Info)

|  |  Byte 1     |  Byte 2   | Byte 3   |
| -----------| ----------- | ----------- | ----------- |
|Message| Switching #  | Time Triggered (Whole #) | Time triggered (Decimal)  |
|Variable Type| uint8_t  | uint8_t  | uint8_t  |
|Min| 0  | 0  | 0  |
|Max| 255 | 255  | 255  |
|Example| 34  | 24  | 55  |

### Message Type 9 (Error)

|  |  Byte 1     |  Byte 2   |
| -----------| ----------- | ----------- |
|Message|   |   |
|Variable Type| uint8_t  | uint8_t  |
|Min|   |   |
|Max|   |   |
|Example|   |   |

### Message Type 10 (Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Reset of Actuator System  |
|Variable Type| uint8_t  | 
|Min| 0  | 
|Max| 1  |
|Example| 1  |