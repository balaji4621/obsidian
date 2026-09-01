---
tags: [sfox, sih2026, master-blueprint]
updated: 2026-08-27
---

# 🏆 SFox Hybrid Infrasound Sensor Master Blueprint
**Sponsoring Agency:** National Technical Research Organisation (NTRO) | **PS ID:** 26144  

---

## 1. Executive Summary & System Architecture
The **SFox Hybrid Architecture** merges physical acoustic engineering and modern edge computing into a single $50\text{ mm} \times 50\text{ mm}$ coin-sized credit-card module:
- **Electronics Platform:** 4-layer FR4 PCB (JLCPCB fabbed, ENIG finish) with AGND/DGND split.
- **Mechanical Acoustic:** Monolithic Isothermal 6061 Aluminum Dual Micro-Chamber Block (5 mL per chamber, shared 2mm thermal divider wall) mounted on PCB.
- **Capillary Leak & Filter:** Calibrated glass micro-capillary ($d = 0.176\text{ mm}$ ID $\times 30\text{ mm}$ length) + 0.2 µm hydrophobic PTFE membrane filter press-fitted into Chamber A $\rightarrow f_c = 0.020\text{ Hz}\ (\tau = 7.96\text{s})$.
- **Thermal Drift Cancel:** Monolithic 6061 Al Isothermal Acoustic Bridge (Chamber A - Chamber B). Identical material conductivity ($k = 160\text{ W/m}\cdot\text{K}$) suppresses thermal drift by **>97%** ($<0.08\text{ Pa/}^\circ\text{C}$).
- **Transduction & AFE:** Piezoresistive Differential Transducer (MPXV7002DP / Honeywell TruStability) + INA128 InAmp (Gain=101.2x) + OPA2188 4th-order Sallen-Key 20Hz LPF + 24-bit ADS1256 ADC. (Digital option: Dual BMP390 direct SPI into ESP32-S3).
- **Edge AI Classifier:** ESP32-S3 running 512-pt sliding FFT ($0.195\text{ Hz/bin}$) + 1D-CNN TensorFlow Lite Micro model (96.25% accuracy across 4 classes in <8.5 ms).
- **Power Autonomy:** <45 mW average power (**>180 hours** runtime on 3.7V 3000 mAh Li-Po).

---

## 2. Signal Flow Matrix
```
  [1.0 Pa Wave @ 5Hz] ──► [4-Arm Porous Hose 1.5m Radial Array (-20dB Wind)]
                      ──► [0.2um PTFE Filter + Chamber A 0.020Hz HPF (Blocks Weather)]
                      ──► [Piezoresistive Differential Sensor MPXV7002DP (1.0 mV/Pa)]
                      ──► [INA128 InAmp (Boosts to 101.2 mV AC)]
                      ──► [OPA2188 20Hz LPF (Kills 50Hz Mains Hum)]
                      ──► [ADS1256 24-bit ADC @ 100 SPS (0.298 uV/bit)]
                      ──► [ESP32-S3 IIR Filter & Sutherland's Engine]
                      ──► [ESP32 512-pt Sliding FFT (0.195 Hz/bin) & TFLite 1D-CNN AI]
                      ──► [Python Live Waterfall UI + Red Banner Alert]
```

---

## 3. Cost & Budgeting
- **Hackathon MVP (Single-Tower Breadboard):** ₹1,900 INR ($23 USD)
- **SFox Hybrid Coin Module (4-Layer PCB):** ₹3,650 INR ($44 USD)
- **Imported Benchmark (Chaparral 64Vx2):** ₹4,50,000 INR ($5,400 USD)
