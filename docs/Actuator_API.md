---
title: Actuator API
tags:
- tag1
- tag2
---

## Message Structure

Start Byte (2 8uint_t)
Sender Address (8uint_t)
Receiver Address (8uint_t)
Message Type (uint8_t)
Message (1-56 8uint_t)
Stop Byte (2 8uint_t)

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

### Message Type 14 (Master Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Master Reset  |
|Variable Type| char  |
|Min| RST |
|Max| RST |
|Example| RST |

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
|Example| 12 | 24 (24 hundreths of a second) |

### Message Type 9 (Error)

|  |  Byte 1     |  Byte 2   |
| -----------| ----------- | ----------- |
|Message| Error Type | Address Received |
|Variable Type| uint8_t  | char |
|Min| 0  | Z (No error address) |
|Max| 5 | Address of Error  |
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

When Actuator Subsystem receives a message, the following is the protocol for handling:

1. Identify start and begin copying it to array for retransmission
2. When Receiver Byte is identified, check if mine or broadcast
    2a. If not mine, finish copying to retransmission array then retransmit
    2b. If mine, continue to step 3
    2c. If broadcast byte, copy to retransmit array, retransmit, and continue to step 3
3. Identify Message Type
4. Utilize message information
5. Trash Message
6. Transmit relevant data
7. Continue from step one when receiving a new message

For each step, there will be an error check to confirm the message is valid. Should it fail, the error code and address it was sent from will be transmitted.