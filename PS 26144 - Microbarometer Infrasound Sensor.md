# 📡 PS ID 26144: Microbarometer Infrasound Sensor (NTRO) Master Note

> **Sponsoring Agency:** National Technical Research Organisation (NTRO)  
> **Target:** Design and construct a ground-up microbarometer detecting sub-20 Hz infrasound (fc = 0.020 Hz, 100 SPS, AFE Gain = 101.2x, 20Hz LPF, STA/LTA trigger).

---

## 🛠️ System Architecture & PDF Optimization Summary
- **Capillary Leak:** $d = 0.288	ext{ mm ID} 	imes 30.0	ext{ mm length}$ for $V = 350	ext{ mL}$ ($C_a = 2.47 	imes 10^{-9}	ext{ m}^3/	ext{Pa}$) $ightarrow f_c = 0.020	ext{ Hz}, 	au = 8.0	ext{s}$.
- **Analog Front-End:** INA128 ($R_g = 499\ \Omega$) + Dual OPA2188 4th-order Sallen-Key LPF ($f_c = 20	ext{ Hz}$) + $1.65	ext{V}$ Vref buffer.
- **Power Optimization:** Disabling OLED during acquisition drops power to $<50	ext{ mW}$, expanding battery life to **$>180	ext{ hours}$** on 3.7V / 3000 mAh Li-Po.
- **DSP & Averaging:** Welch 4-spectrum 50% overlap FFT averaging gives $+6	ext{ dB}$ SNR boost, detecting tones down to $22	ext{ mPa}$.
- **Thermal Compensation:** Sutherland's law $\mu(T)$ tracking in `src/adaptive_iir_thermal.cpp` compensates for $\pm 8.6\%$ viscosity shift.

---

## 📚 Navigation Links
- [[00_Master_Architecture_and_Deep_Analysis]]
- [[01_Physics_and_Fundamentals]]
- [[02_Mechanical_Transducer_Build]]
- [[03_Basic_Circuit_and_AFE_Build]]
- [[04_Digitization_and_DSP_Firmware]]
- [[05_Step_by_Step_Assembly_and_Testing_Playbook]]
- [[full_engineering_analysis_report]]

---

## 💰 Budget Options
- **Hackathon MVP:** **₹1,900 INR** (~$23 USD)
- **Production Spec:** **₹48,000 INR** (~$580 USD)
