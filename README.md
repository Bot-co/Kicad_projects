# 🔌 Custom ATtiny85 USB Development Board

A compact USB-powered development board built around the **ATtiny85-20S** microcontroller.  
The design includes USB data-line protection, an onboard LED, decoupling capacitor, and two GPIO header connectors for easy prototyping.

This is my own minimal version of a Digispark-style board, fully designed in **KiCad** from scratch.

---

## 📌 Features

- **Microcontroller:** ATtiny85-20S (SOIC-8)
- **USB Interface:** Direct USB pads on PCB  
  - Zener-diode protection on D+ / D−  
  - 1.5k USB pull-up resistor
- **Power:** 5V from USB
- **I/O:**  
  - Header **J1** (PB0, PB1, PB2, PB3)  
  - Header **J2** (PB4, PB5, GND, VCC)
- **Onboard LED:** Connected to PB0 (via R3 330Ω)
- **Decoupling capacitor:** 100nF near VCC
- **Compact PCB layout with USB edge connector**

---

## 🛠 Schematic Overview

Key components used:

| Component | Function |
|----------|----------|
| ATtiny85-20S | Main microcontroller |
| C1 100nF | Power supply decoupling |
| D1, D2 (3.6V Zener) | USB D+ / D− protection |
| R4 1.5k | USB pull-up (D+) |
| R1, R2 (68Ω) | USB D+ / D− series resistors |
| R3 330Ω | LED current limiting |
| D3 LED | Status indicator |
| J1 / J2 | Expansion headers |

USB pads route directly to D+ and D− via the standard Digispark-style resistor/zener configuration.

---

## 📐 PCB

The PCB is designed to plug directly into a USB Type-A port.  
Major layout highlights:

- Short trace routing for USB lines  
- Zener diodes placed close to USB pads  
- Decoupling capacitor placed near ATtiny VCC pin  
- LED positioned on the top side for visibility  
- Two 4-pin headers (J1 and J2) for GPIO access  
- Clean ground plane and simple 2-layer routing

Renders are available in `/docs/`:

- `top.png`  
- `bottom.png`

(You can export your own and place them here.)

---

## 🔌 Pinout

| Pin | ATtiny85 Function | Connected To |
|-----|--------------------|--------------|
| PB0 | I/O / PWM | LED (via R3) + J1 |
| PB1 | I/O | J1 |
| PB2 | I/O | J1 |
| PB3 | I/O | J1 |
| PB4 | I/O | J2 |
| PB5 | RESET / I/O | J2 |
| VCC | 5V | USB VBUS |
| GND | Ground | USB GND |

---

## 💾 Programming

This board uses the ATtiny85-20S, which supports:

- **USBasp**
- **Arduino as ISP**
- **AVRDUDE**
- **Micronucleus bootloader**
