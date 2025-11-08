# Software (how the Cadio-based firmware works)

**Summary**  
This project uses the Cadio platform and the Cadio dynamic firmware running on the ESP32. The device is managed and controlled through the Cadio app/platform (not via raw HTTP endpoints). The Cadio firmware exposes the device’s capabilities (ON/OFF relays, sensors, etc.) to the Cadio cloud/app and handles communication, configuration, and remote access. :contentReference[oaicite:0]{index=0}

---

## 1. Overall architecture
- **ESP32 + Cadio firmware**: the ESP32 runs the Cadio dynamic firmware (pre-built or flashed via Cadio Flasher). The firmware implements the Cadio unit protocol so the device can be discovered, configured and controlled by the Cadio app. :contentReference[oaicite:1]{index=1}  
- **Cadio app / cloud**: you use the Cadio app (or the Cadio cloud) to add the unit, configure devices (relays), create actions, and trigger those actions from the phone or voice assistants. The app is the control plane; the unit is the data/actuation plane. :contentReference[oaicite:2]{index=2}

---

## 2. What the firmware exposes (device model)
Cadio units are built around a standard device model: a unit can expose multiple *devices* (for example: ONOFF relays, dimmers, sensors, RGB, etc.). In your case the relays are represented as ON/OFF devices in the Cadio unit configuration. The Cadio web/app UI lets you map each physical relay GPIO to a logical device entry. :contentReference[oaicite:3]{index=3}

---

## 3. How control works (no raw HTTP required)
- **No manual HTTP**: Control is done using the Cadio app or via Cadio’s built-in integrations (voice assistants, remote access). You do not need to implement or call HTTP endpoints from outside — Cadio handles the protocol between the app and the ESP32 unit. :contentReference[oaicite:4]{index=4}  
- **App actions / voice**: In the Cadio app you create actions (for example, “Turn on Relay 1”) and map them to the device. Those actions can be triggered manually, via voice (Google/Alexa if configured), or by Cadio automations.

---

## 4. Flashing & provisioning
- **Flashing**: Use the Cadio Flasher tool or Cadio’s recommended flashing method to install the Cadio dynamic firmware on your ESP32. The flasher automates the correct binary and settings for supported boards. :contentReference[oaicite:5]{index=5}  
- **First-time provisioning**: After flashing the device normally boots into configuration (or config AP) mode where you can connect with the Cadio app and supply Wi-Fi credentials and unit settings. See the Cadio “info file / general settings” documentation for options like config AP name and device authorization. :contentReference[oaicite:6]{index=6}

---

## 5. Extending or customizing behaviour
If you need functionality that the standard Cadio firmware does not provide, Cadio supports these extension paths:
- **CadioSerial / external MCU**: If you need more GPIOs or to offload logic, you can use an external MCU and the CadioSerial Arduino library to let the Cadio unit talk to that MCU. This is useful for custom hardware or special timing-critical tasks. :contentReference[oaicite:7]{index=7}  
- **Custom firmware (advanced)**: For maximum control you can fork or write custom firmware that implements the Cadio unit protocol or communicates with the Cadio cloud, but that is an advanced workflow and not required for normal use.

---

## 6. Recommended file references in this repo
- `firmware/` — Keep a note (or the Cadio-flashed `.bin`) here if you want others to be able to flash the exact binary you used (upload the binary as a Release asset, not as a tracked build folder). :contentReference[oaicite:8]{index=8}  
- `docs/cadio-setup.md` — Step-by-step on how you flashed and configured the unit in the Cadio app (include screenshots and the exact device mapping).  
- `docs/hardware.md` — GPIO-to-relay mapping and power notes (so others can match logical devices in the app to your physical relays).

---

## 7. Security & notes
- Do not include Wi-Fi credentials or private tokens in repository source files. Use the Cadio app provisioning to set Wi-Fi credentials at runtime. :contentReference[oaicite:9]{index=9}  
- If you plan to share the compiled `.bin`, provide a checksum (`CHECKSUMS.txt`) so others can verify authenticity.

---

## Useful Cadio docs (readers / maintainers)
- Cadio firmware & flasher: Cadio Docs — ESP32 firmware. :contentReference[oaicite:10]{index=10}  
- Concepts & supported devices (ONOFF, RGB, sensors): Cadio Concepts. :contentReference[oaicite:11]{index=11}  
- Info file / general settings (provisioning modes): Cadio Info File docs. :contentReference[oaicite:12]{index=12}
