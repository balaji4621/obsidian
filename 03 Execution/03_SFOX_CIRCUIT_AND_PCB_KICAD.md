---
tags: [sfox, sih2026, circuit-pcb]
updated: 2026-08-27
---

# 🔌 SFox Module 03: Dual-Architecture Circuit Schematic & PCB Layout

## 1. PCB Specifications
- **Dimensions:** $50.0\text{ mm} \times 50.0\text{ mm} \times 1.6\text{ mm}$ (ENIG Gold Finish, JLCPCB Fabbed).
- **Layer 1 (Top):** Analog signals + Driven Guard Rings + Power rails + Sensor Pads.
- **Layer 2 (AGND):** Solid Unbroken Analog Ground Plane.
- **Layer 3 (PWR):** TPS7A4700 3.3V Power Plane + Digital Ground (DGND) split.
- **Layer 4 (Bottom):** Digital signals + ESP32-S3 Microcontroller + Antenna.

---

## 2. Sensor Interface Dual Architecture
- **Analog Chain (High-Speed TinyML):** Piezoresistive Differential Pressure Transducer (MPXV7002DP / Honeywell TruStability) feeds continuous analog signals $V_{in+}, V_{in-}$ directly into INA128PA InAmp ($101.2\text{x}$ Gain) $\rightarrow$ OPA2188 20Hz LPF $\rightarrow$ ADS1256 24-bit ADC.
- **Digital Chain (Secondary Reference):** Dual BMP390 barometric sensors connected to ESP32-S3 over SPI/I2C for digital IIR baseline tracking, ambient temp/pressure monitoring, and Sutherland's Law air viscosity calculations.

---

## 3. Circuit Diagrams
- Interactive Web Schematic: `sfox_circuit_viewer.html`
- Scalable Vector Graphic: `sfox_full_circuit_schematic.svg`
- Pin-by-pin schematic text reference: [[07_SFOX_COMPLETE_CIRCUIT_SCHEMATIC_DIAGRAM]]
