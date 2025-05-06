---
title: Actuator API
tags:
- tag1
- tag2
---

## Message Structure

Start Byte (2 uint8_t)

Sender Address (uint8_t)

Receiver Address (uint8_t)

Message Type (uint8_t)

Message (1-56 uint8_t)

Stop Byte (2 uint8_t)

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
|Dominick Trusko| D |
| Broadcast | X |

## Recieved Messages

### Message Type 5 (Master Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Master Reset  |
|Variable Type| uint8_t |
|Min| 1 |
|Max| 1 |
|Example| 1 |

### Message Type 7 (Speed Setting from HMI)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Speed Setting  |
|Variable Type| uint8_t  |
|Min|  1 |
|Max|  3 |
|Example| 2 (Medium Speed)|

## Sent Messages

### Message Type 3 (Error)

|  |  Byte 1     | 
| -----------| ----------- | 
|Message| Error Type |
|Variable Type| char | uint8_t  |
|Min| 1  | 
|Max| 5 | 
|Example| 2  |

Error Types:

1: Incorrect / No Start Bit

2: Incorrect / No Address Bit

3: Incorrect / No Message Type

4: Incorrect Data Value in Valid Message

5: Bytes per Message Overflow

## Code Handling

Since there are no actuator messages other than errors, all retransmissions take priority

When Actuator Subsystem receives a message, the following is the protocol for handling:

1. Copy incoming message to array to check if it fits API format / is valid
2. After message is copied to array, check begin error check
3. When no errors for bytes 1-3, check receiver address:

    3a. If not mine, retransmit

    3b. If mine, continue to step 3

    3c. If broadcast byte, retransmit message, and continue to step 4
    
4. Utilize message information (When applicable)
5. Trash Message (Done automatically when next message is received)
6. Transmit if message is not for me or broadcast
7. If there is an error, transmit
8. Continue from step one when receiving a new message

For each step, there will be an error check to confirm the message is valid. Should it fail, the error code and address it was sent from will be transmitted.

Should characters be sent outside of start or stop bits, they are ignored and trashed.

For error handling and reset:

When reset is received:

- Halt system and do software reinitialization

When error is received:

- Retransmit, continue if possible otherwise wait for reset