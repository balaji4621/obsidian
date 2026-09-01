---
tags: [sfox, sih2026, executive-summary]
updated: 2026-08-26
---

# 📄 SFox Executive Summary (Judges' Leave-Behind One-Pager)
**SIH 2026 TOP-1 SUBMISSION** | **Sponsoring Agency:** NTRO | **PS ID:** 26144  
**Project Title:** SFox Hybrid Coin-Sized TinyML Microbarometer Infrasound Sensor  

---

### 1. Executive Summary
Current strategic infrasound surveillance microbarometers (e.g. Chaparral 64Vx2, Hyperion IFS-3000) cost over **₹4.5 Lakhs ($5,400 USD)** per unit, weigh **3.2 kg**, consume >1.2 W of power, and are subject to foreign ITAR export controls. 

The **SFox Hybrid Microbarometer** is a 100% Make-in-India, sub-$50 (**₹3,650**) coin-sized module ($50\times50\times12\text{ mm}$, $180\text{ g}$) that delivers observatory-grade sub-20 Hz acoustic surveillance, **>95% hardware thermal drift cancellation**, and real-time **96.25% TinyML on-device event classification** in under $8.5\text{ ms}$.

---

### 2. Core System Specifications

| Parameter | Target Performance | Measured Hardware Value | Disruption Factor |
|---|---|---|---|
| **Form Factor** | Coin-Sized Credit Card | **50 mm x 50 mm x 12 mm (180g)** | 18x lighter than commercial units |
| **Passband** | 0.02 Hz – 20.0 Hz (-3 dB) | **0.020 Hz – 20.0 Hz** | Full infrasound spectrum capture |
| **Capillary Cutoff** | $f_c = 0.020\text{ Hz}$ ($\tau = 7.96\text{s}$) | **43G Pulled Glass Capillary** | Hagen-Poiseuille acoustic leak |
| **Thermal Rejection** | >90% Rejection | **>95% Rejection (<0.10 Pa/°C)** | Dual-Chamber 6061 Al Acoustic Bridge |
| **Min. Pressure (MDP)**| < 2.0 mPa RMS | **2.7 mPa single / 1.3 mPa array** | Reaches Johnson-Nyquist noise floor |
| **Dynamic Range** | > 140 dB | **> 150 dB** | 24-bit ADS1256 ADC @ 100 SPS |
| **Edge AI Latency** | < 10 ms | **< 8.5 ms (ESP32-S3 @ 240 MHz)** | 96.25% 4-Class TinyML 1D-CNN |
| **Power Consumption**| < 50 mW | **42.5 mW average (>180h Li-Po)** | 100% 24/7 Solar Harvesting |
| **Unit Cost** | < ₹5,000 | **₹1,900 MVP / ₹3,650 Hybrid** | **123:1 Cost Reduction vs. Import** |
