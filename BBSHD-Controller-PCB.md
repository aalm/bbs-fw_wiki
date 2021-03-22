

## Hardware Revisions

Revision | MCU          | Released    | Comment
-------- | ------------ | ----------- | --------------------
V1.4     | STC15W4K56S4 | ~2017       | V1.3 printed on PCB
V1.5     | IAP15W4K61S4 | ~2019       | V1.4 printed on PCB




## Pinout

### STC

PIN  | Type  | Function               | Comment
-----| ----- | -----------------------| --------------------
P1.3 | ADC3  | Throttle input         | 0-5V. 9K external pulldown.
P2.0 | OUT   | Motor power enable     | Signal to NEC MCU to enable motor power.
P2.1 | OUT   | Motor control enable   | Signal to NEC MCU to enable motor control (should be kept high).
P2.3 | OUT   | External lights        | Controls power to secondary power pcb to drive external lights
P2.4 | IN    | Brake                  | 5V. Active low. Also connected directly to NEC MCU.
P3.0 | UART1 | RX                     | 5V. External UART rx line for display communication.
P3.1 | UART1 | TX                     | 5V. External UART tx line for display communication.
P4.4 | OUT   | Motor control enable   | Signal to NEC MCU to enable motor control (should be kept high).














### NEC














