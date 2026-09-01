---
tags: [sfox, sih2026, master-blueprint]
updated: 2026-08-26
---

# 🏆 SFox Hybrid Coin-Sized TinyML Microbarometer Infrasound Sensor
**Sponsoring Agency:** National Technical Research Organisation (NTRO) | **PS ID:** 26144  

---

## 📌 Executive Summary & Architecture
The **SFox Hybrid Architecture** merges physical acoustic engineering and modern edge computing into a single $50\text{ mm} \times 50\text{ mm}$ coin-sized credit-card module:
- **Electronics Platform:** 4-Layer FR4 PCB (JLCPCB fabbed, ENIG finish) with solid AGND plane, DGND split, and driven guard rings.
- **Mechanical Transducer:** Dual micro-chamber (5 mL per chamber) mounted directly on PCB top layer (SLA Resin Chamber A + 6061 Aluminum Chamber B).
- **Capillary Leak:** 43G pulled glass capillary ($d = 0.176\text{ mm}$ ID, $L = 30.0\text{ mm}$) press-fitted into Chamber A $\rightarrow R_a = 2.25 \times 10^{11}\text{ Pa}\cdot\text{s/m}^3, C_a = 3.53 \times 10^{-11}\text{ m}^3/\text{Pa} \rightarrow f_c = 0.020\text{ Hz}\ (\tau = 7.96\text{s})$.
- **Thermal Drift Cancellation:** Dual-Chamber Acoustic Bridge suppresses thermal drift by **>95%** in hardware ($<0.10\text{ Pa/}^\circ\text{C}$).
- **Analog Front-End (AFE):** INA128 Instrumentation Amp (Gain=101.2x) + OPA2188 4th-order Sallen-Key LPF ($f_c = 20\text{ Hz}$) + ADS1256 24-bit ADC.
- **Edge AI Classifier:** ESP32-S3 running 1D-CNN TensorFlow Lite Micro model (96.25% accuracy across 4 classes in <8.5 ms).
- **Power Autonomy:** <45 mW average power (**>180 hours** on 3.7V 3000 mAh Li-Po).
- **Unit Production Cost:** **₹1,900 MVP** | **₹3,650 Hybrid Coin Module**.

---

## 🔗 Execution Submodules
- [[00_SFOX_MASTER_BLUEPRINT]] — Executive Summary & Signal Flow Matrix.
- [[01_SFOX_PHYSICS_AND_MATH]] — First-Principles Fluid Dynamics & Noise Limits.
- [[02_SFOX_CAD_AND_MECHANICAL_DESIGN]] — OpenSCAD Dual-Chamber Code.
- [[03_SFOX_CIRCUIT_AND_PCB_KICAD]] — KiCad 4-Layer ENIG PCB Layout & Netlist.
- [[04_SFOX_FIRMWARE_TINYML_DSP]] — ESP32-S3 C++ Source Code & TFLite Model.
- [[05_SFOX_TESTING_PROOF_AND_PITCH]] — Validation Tests & Stage Pitch Script.
- [[06_SFOX_COMPLETE_PROCUREMENT_ORDER_LIST]] — Complete JLCPCB & Parts List.
- [[07_SFOX_COMPLETE_CIRCUIT_SCHEMATIC_DIAGRAM]] — Full Electrical Circuit Diagram.
