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
| Broadcast | X |

## Recieved Messages

### Message Type 14 (Master Reset)

|  |  Byte 1     |
| -----------| ----------- |
|Message| Master Reset  |
|Variable Type| uint8_t |
|Min| 1 |
|Max| 1 |
|Example| 1 |

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

|  |  Byte 1     | 
| -----------| ----------- | 
|Message| Error Type |
|Variable Type| uint8_t  |
|Min| 0  | |
|Max| 5 | 
|Example| 2  |

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

Priority is placed on retransmitting incoming data before transmitting personal data as the outgoing Actuator data is not time sensitive (other than errors).

When Actuator Subsystem receives a message, the following is the protocol for handling:

1. Identify start and begin copying it to array for retransmission
2. After message is copied to array, check begin error check
3. When no errors for bytes 1-3, check receiver address:

    3a. If not mine, retransmit

    3b. If mine, continue to step 3

    3c. If broadcast byte, retransmit message, and continue to step 4
    
4. Utilize message information
5. Trash Message (Done automatically when next message is received)
6. Transmit relevant data when not transmitting priority data
7. Continue from step one when receiving a new message

For each step, there will be an error check to confirm the message is valid. Should it fail, the error code and address it was sent from will be transmitted.

Should characters be sent outside of start or stop bits, they are ignored and trashed.

To elaborate on step 6 and error handling

1. Whenever an interruptive event occurs (ie  error or reset) identify and redirect to appropriate function
2. 
5. 
6. Check if already transmitting, if so wait for transmission to end and delay then send
7. Otherwise send
8. If error:

    8a. When mine, sends hardcoded error to MQTT
    8b. If other error, retransmitted as normal

9. If reset message, halt system and retransmit to MQTT

A group sending schedule may be implemented to improve message success rates and ensure minimal message loss.