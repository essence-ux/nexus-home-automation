# NEXUS-HOME-AUTOMATION
# Hardware Overview

This directory contains the hardware-related documentation and references for the **Nexus Home Automation** project.  
The project uses a **Cadio Dynamic Module** paired with a **4-channel relay board** to automate the control of multiple AC or DC loads.

---

## 1. Bill of Materials (BOM)

A detailed list of all components and tools used in this project is provided in the [BOM file](hardware/bom.csv).  
Each component includes a short description, basic specifications, and approximate pricing in INR.

Key components include:
- Cadio Dynamic Module (controller)
- 4-Channel 5V Relay Board
- 5V Power Supply
- Jumper wires (male-female)
- Optional components: breadboard, screw terminals, enclosure, and multimeter for testing

Refer to the `bom.csv` file for full details and quantities.

---

## 2. Relay Board and Wiring Summary

The relay board interfaces directly with the output pins of the Cadio module.

| Relay Channel | Cadio Pin | Function | Typical Load |
|----------------|-----------|-----------|---------------|
| Relay 1 | GPIO 25 | Switches Load 1 | Light or Fan |
| Relay 2 | GPIO 26 | Switches Load 2 | Light or Fan |
| Relay 3 | GPIO 27 | Switches Load 3 | Light or Fan |
| Relay 4 | GPIO 14 | Switches Load 4 | Light or Fan |

**Power and Ground Connections**
- Relay VCC → 5V supply  
- Relay GND → Common ground with Cadio module  
- Cadio module powered via USB or 5V adapter  

Ensure all grounds are common between the relay module and the controller.

---

## 3. Power and Load Specifications

- **Input Voltage (logic side):** 5V DC  
- **Relay Output Ratings:** 10A at 250V AC or 10A at 30V DC (max per channel)  
- **Recommended Adapter:** 5V, 2A regulated DC adapter  
- **Total Current Draw:** Approx. 500–700 mA (relays ON)  

Always verify your relay board specifications, as coil current and logic levels can vary between models.

---

## 4. Safety Precautions

- Maintain electrical isolation between the **AC load wiring** and the **low-voltage control circuit**.  
- Never connect or disconnect live AC loads during operation.  
- Use insulated connectors and avoid loose wires.  
- If you are not familiar with handling AC wiring, perform tests only with low-voltage DC loads.

---

## 5. Optional Additions

- **Enclosure:** Use a plastic or ABS box to mount the relay and Cadio board for a professional finish.  
- **Screw Terminal Connectors:** For reliable relay-to-load connections.  
- **Indicator LEDs:** Optional front-panel indicators can be wired to relay outputs for status display.

---

## 6. References

- [Cadio Documentation](https://egycad.com/cadio)  
- [Relay Module Datasheet]([https://components101.com/modules/5v-4-channel-relay-module](https://components101.com/switches/5v-single-channel-relay-module-pinout-features-applications-working-datasheet))  
- [Cadio Flasher Tool]([https://www.cadio.io/flasher](https://docs.espressif.com/projects/esp-test-tools/en/latest/esp32/production_stage/tools/flash_download_tool.html))

---


