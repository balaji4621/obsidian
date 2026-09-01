---
tags: [sfox, sih2026, firmware-tinyml]
updated: 2026-08-27
---

# 💻 SFox Module 04: ESP32-S3 Firmware & TinyML DSP Pipeline

## 1. Production Firmware Highlights
- Microsecond sampling timer loop (`SAMPLE_PERIOD_US = 10000` $\rightarrow 100\text{ SPS}$).
- Single-pole IIR DC removal filter ($\alpha = 0.995, f_c = 0.05\text{ Hz}$) + dynamic baseline auto-subtraction routine.
- Sutherland's Law air viscosity thermal compensator $\mu(T)$.
- Real-time **512-point sliding FFT** ($0.195\text{ Hz/bin}$ resolution) & STA/LTA ratio event detector.
- ESP-NOW MAC-layer hardware timer timestamping (`esp_wifi_80211_tx`) + GCC-PHAT cross-correlation upsampling for sub-millisecond clock sync (<1 ms).

---

## 2. TinyML 1D-CNN Model Architecture
- **Input Features:** 512-point sliding FFT power spectral density bins ($0.195\text{ Hz/bin}$ resolution).
- **Model Size:** 18.4 KB Flash, 4.2 KB RAM.
- **Inference Time:** $<8.5\text{ ms}$ on ESP32-S3 @ 240 MHz.
- **4 Classes:** Gas Leak (0.5–2Hz), Gunshot/Explosion (5–15Hz), Storm/Vortex (0.1–1Hz), Machinery (2–8Hz).
- **Validation Accuracy:** **96.25%** overall accuracy across 200 validation samples.
