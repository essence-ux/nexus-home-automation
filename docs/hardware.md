# Hardware Setup

## Components Used
- ESP32 Dev Board
- 4-Channel Relay Module
- 5V Power Supply
- Jumper Wires

## Pin Connections
| Relay Channel | ESP32 GPIO |
|----------------|------------|
| Relay 1 | GPIO 25 |
| Relay 2 | GPIO 26 |
| Relay 3 | GPIO 27 |
| Relay 4 | GPIO 14 |

## Power Notes
- Relay board VCC → 5V  
- GND (ESP32 & Relay) must be common.  
- Each relay can switch up to 10A at 250V AC (max).

> ⚠️ **Safety:** Never connect mains power while wiring. Double-check polarity before powering the relay board.
