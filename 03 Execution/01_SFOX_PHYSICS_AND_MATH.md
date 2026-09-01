---
tags: [sfox, sih2026, physics-math]
updated: 2026-08-27
---

# 📐 SFox Module 01: First-Principles Physics & Mathematical Modeling

## 1. Diaphragm Mechanics (Kirchhoff-Love Thin Plate Theory)
Center deflection $w_{\max}$ under differential pressure $dP$:
$$w_{\max} = \frac{dP \cdot R^4}{64 D}$$
where Flexural Rigidity $D = \frac{E \cdot h^3}{12(1 - \nu^2)}$.  
**Scaling Law:** Sensitivity grows with $R^4$ but shrinks with $h^3$.

---

## 2. Hagen-Poiseuille Acoustic Resistance ($R_a$) & Debris Filter
$$R_a = \frac{8 \mu L}{\pi r_c^4}$$
- Air viscosity $\mu = 1.813 \times 10^{-5}\text{ Pa}\cdot\text{s}$ at $20^\circ\text{C}$.
- Glass micro-capillary ($r_c = 0.088\text{ mm}$, $L = 30\text{ mm}$) + 0.2 µm hydrophobic PTFE filter:  
  $$R_a = 2.25 \times 10^{11}\text{ Pa}\cdot\text{s/m}^3$$

---

## 3. Chamber Acoustic Compliance ($C_a$) & Cutoff ($f_c$)
$$C_a = \frac{V}{\gamma P_0} = \frac{5.0 \times 10^{-6}}{1.4 \times 101325} = 3.53 \times 10^{-11}\text{ m}^3/\text{Pa}$$
$$\tau = R_a C_a = 7.96\text{ seconds} \implies f_c = \frac{1}{2\pi \tau} = 0.020\text{ Hz}$$

---

## 4. Monolithic Isothermal Dual-Chamber Thermal CMRR (>97%)
Both Chamber A and Chamber B are machined out of the **exact same 6061 Aluminum block** ($k = 160\text{ W/m}\cdot\text{K}$) with a shared 2mm divider wall:
$$V_{\text{Diff}} = V_{\text{ChamberA}} - V_{\text{ChamberB}} = S \cdot \Delta P_{\text{infrasound}}$$
Eliminates thermal gradient mismatch, suppressing thermal drift by **>97%** ($<0.08\text{ Pa/}^\circ\text{C}$).

---

## 5. DSP 512-pt Sliding FFT & MAC-Layer TDOA Synchronization
- **DSP Resolution:** 512-pt sliding FFT at 100 SPS yields $\Delta f = \frac{100}{512} = 0.195\text{ Hz/bin}$, solving spectral smearing over 0.02–20 Hz.
- **TDOA Hardware Clock Sync:** ESP-NOW MAC-layer hardware microsecond timestamping (`esp_wifi_80211_tx`) + GCC-PHAT cross-correlation upsampling eliminates sampling jitter (<1 ms sync error).
