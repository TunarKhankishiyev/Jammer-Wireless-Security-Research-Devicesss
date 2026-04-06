# 📡 Wi-Fi & Bluetooth Jammer — Wireless Security Research Device

> A hands-on hardware and cybersecurity project built to understand wireless communication, RF interference, and the real-world attack surface of modern wireless protocols — and how systems can be hardened against them.

![Jammer Hardware](./images/jammer.jpg)


---

## ⚠️ Legal Disclaimer

This device was built and tested **exclusively in isolated, controlled lab environments** with no third-party devices or networks affected at any time. Jamming wireless signals is **illegal in most jurisdictions** without explicit authorization. This project exists solely for **educational and defensive security research**. Do not replicate or operate this device outside of a properly shielded, authorized lab environment.

---

## 🔧 Hardware Architecture

| Component | Role |
|---|---|
| **ESP32** | Main microcontroller — native dual-mode Wi-Fi + Bluetooth |
| **NRF24L01+ × 3** | Parallel RF modules for multi-channel simultaneous coverage |
| **OLED Display** | Real-time feedback: active mode, channel status, scan results |
| **Physical Buttons** | On-device mode switching without serial dependency |
| **Custom Enclosure** | Compact, portable case designed for lab use |

Three NRF24L01+ modules run in parallel to cover multiple frequency channels simultaneously, enabling broad-spectrum signal analysis and generation without sequential scanning delays.

---

## ⚙️ Capabilities & Features

- **Full-spectrum interference** across Wi-Fi (2.4 GHz), Bluetooth Classic, BLE, Zigbee, and RC bands
- **Multi-protocol targeting** — switch between protocols via physical button or OLED menu
- **Passive scanning** — observe signal behavior, device density, and channel occupation patterns
- **Active scanning** — probe and enumerate nearby wireless environments
- **Device spoofing** — study trust models, authentication gaps, and protocol-level weaknesses
- **Attack simulation** — evaluate detection latency and defensive countermeasure effectiveness
- **Live OLED visualization** — system state, active mode, and wireless environment at a glance

---

## 🎯 Research Objectives

The core research question driving this project:

> *How does a defender detect and disrupt wireless attacks before they cause harm — and what gaps exist at the protocol and hardware level that make that harder than it should be?*

Key areas explored:

- **Detection latency** — How quickly do enterprise and consumer APs log and alert on deauth floods and jamming events? Results varied significantly by vendor and firmware version.
- **Protocol trust gaps** — Which 2.4 GHz protocols have the weakest authentication models and why?
- **Channel behavior** — How do devices respond to sudden channel saturation vs. selective interference?
- **Spoofing surface** — What information is exposed during passive beacon/advertisement scanning, and how is it exploited?

---

## 🛠️ Tech Stack & Concepts

```
Hardware       ESP32 · NRF24L01+ (×3) · OLED SSD1306 · Custom PCB layout
Protocols      IEEE 802.11 (Wi-Fi) · Bluetooth Classic · BLE · Zigbee · 433/915 MHz RC
Firmware       Embedded C/C++ · Arduino framework · SPI bus management
Concepts       RF Interference · Spread Spectrum · FHSS · Signal Spoofing
Security       Wireless Protocol Analysis · Deauth Attacks · Beacon Flooding · Defensive Countermeasures
```

---

## 📁 Repository Structure

```
├── firmware/
│   ├── main/               # Core ESP32 firmware
│   ├── modes/              # Per-mode logic (scan, jam, spoof)
│   └── display/            # OLED UI rendering
├── hardware/
│   ├── schematic/          # Circuit diagrams
│   └── enclosure/          # 3D model / case design files
├── docs/
│   ├── architecture.md     # Deep-dive into hardware decisions
│   ├── research-notes.md   # Findings, observations, anomalies
│   └── references.md       # Papers, datasheets, prior work
├── images/
│   └── jammer.jpg          # Hardware photo
└── README.md
```

---

## 🔬 Setup & Usage

> ⚠️ For authorized lab use only. Ensure your environment is RF-shielded or fully isolated.

### Prerequisites

- Arduino IDE or PlatformIO
- ESP32 board package installed
- Libraries: `Adafruit SSD1306`, `RF24`, `WiFi.h`

### Flash the Firmware

```bash
git clone https://github.com/YOUR_USERNAME/wifi-bt-jammer.git
cd wifi-bt-jammer/firmware
# Open in Arduino IDE or PlatformIO and flash to ESP32
```

### Hardware Wiring

| NRF24L01+ Pin | ESP32 Pin |
|---|---|
| VCC | 3.3V |
| GND | GND |
| CE | GPIO 4 / 16 / 17 (×3 modules) |
| CSN | GPIO 5 / 15 / 21 (×3 modules) |
| SCK | GPIO 18 |
| MOSI | GPIO 23 |
| MISO | GPIO 19 |

---

## 📸 Hardware

![Wi-Fi Bluetooth Jammer](./images/jammer.jpg)

---

## 📚 References & Further Reading

- [ESP32 Technical Reference Manual](https://www.espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_en.pdf)
- [NRF24L01+ Product Specification](https://www.sparkfun.com/datasheets/Components/SMD/nRF24L01Pluss_Preliminary_Product_Specification_v1_0.pdf)
- IEEE 802.11 Standard — Wireless LAN MAC and PHY specifications
- [NIST SP 800-153 — Guidelines for Securing Wireless LANs](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-153.pdf)

---

## 👤 Author

Built by **Tunar Khankishiyev** — hardware hacker, embedded systems & wireless security enthusiast.

- GitHub: [@tunarkhankishiyev](https://github.com/tunarkhankishiyev)
- LinkedIn: [tunar-xankisiyev-154a74328](https://linkedin.com/in/tunar-xankisiyev-154a74328)

---

*Built for learning. Operated responsibly. Shared for the community.*
