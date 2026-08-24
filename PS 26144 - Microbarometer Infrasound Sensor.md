# 📡 PS ID 26144: Microbarometer Infrasound Sensor (NTRO)

> **Sponsoring Agency:** National Technical Research Organisation (NTRO)  
> **Category:** Hardware | **Theme:** Precision Sensors / Strategic Monitoring  
> **Core Objective:** Design and fabricate a custom microbarometer from scratch to detect sub-20 Hz atmospheric pressure waves (explosions, volcanoes, rocket launches) while rejecting wind noise and thermal drift.

---

## 🧠 Module Overview & Navigation

### 1. 🔬 [[01_Physics_and_Fundamentals]]
- **Wavelengths:** Sub-20 Hz waves have wavelengths $>34	ext{ meters}$, allowing them to travel $1,000	ext{s of km}$ without obstacle blocking.
- **Capillary Leak Physics:** Hagen-Poiseuille law $R_a = rac{128\mu L}{\pi d^4}$ creates an acoustic high-pass filter $f_c = rac{1}{2\pi R_a C_a} = 0.02	ext{ Hz}$.
- **Wheatstone Bridge & Op-Amps:** Differential sensing cancels thermal drift; zero-drift OPA2188 eliminates $1/f$ flicker noise.

### 2. 🛠️ [[02_Mechanical_Transducer_Build]]
- **Chamber:** $350	ext{ mL}$ sealed acrylic/PVC chamber ($4	ext{mm}$ wall thickness).
- **Capillary Leak:** $27	ext{-Gauge}$ stainless steel needle ($d=0.21	ext{mm}, L=30	ext{mm}$) tuned to $	au = 8	ext{ seconds}$ decay time.
- **Windscreen Array:** 4-arm porous soaker hose rosette ($1.0	ext{m}$ aperture) rejecting wind noise by $>20	ext{ dB}$.

### 3. ⚡ [[03_Basic_Circuit_and_AFE_Build]]
- **Stage 1 (InAmp):** INA128 ($R_g = 499\ \Omega$, Gain $= 101.2	ext{x}$, CMRR $>100	ext{ dB}$).
- **Stage 2 (Vref Bias):** OPA2188 op-amp buffer providing $1.65	ext{V}$ mid-supply reference.
- **Stage 3 (LPF Filter):** 4th-order Sallen-Key Butterworth LPF ($f_c = 20	ext{ Hz}$, $R=11.3	ext{k}\Omega, C1=1\mu	ext{F}, C2=390	ext{nF}$).
- **Power Integrity:** TPS7A4700 ultra-low noise LDO + star grounding.

### 4. 💻 [[04_Digitization_and_DSP_Firmware]]
- **ADC:** ADS1115 ($16	ext{-bit}$, $250	ext{ SPS}$) or ADS1256 ($24	ext{-bit}$, $100	ext{ SPS}$).
- **Firmware:** ESP32-S3 $100	ext{ Hz}$ microsecond timer loop + $0.05	ext{ Hz}$ DC removal IIR filter + STA/LTA trigger algorithm.
- **Dashboard:** Real-time Python PyQtGraph/Matplotlib waterfall heatmap UI.

### 5. 🎯 [[05_Step_by_Step_Assembly_and_Testing_Playbook]]
- **Validation Tests:** Syringe Tap Decay, Balloon Pop Impulse, Fan Wind Rejection, Speaker Frequency Sweep.
- **3-Minute Pitch Script:** Hook $ightarrow$ Problem $ightarrow$ Hardware Walkthrough $ightarrow$ Balloon Pop Live Demo $ightarrow$ Closing Vision.

---

## 📊 Numerical Signal Trace (1.0 Pa Wave @ 5 Hz)
`1.0 Pa Air Wave` $ightarrow$ `Porous Hose Array (-20dB Wind)` $ightarrow$ `Chamber 0.02Hz HPF` $ightarrow$ `MPXV7002 Sensor (1.0 mV)` $ightarrow$ `INA128 InAmp (101.2 mV)` $ightarrow$ `4th-Order LPF (20Hz Cutoff)` $ightarrow$ `ADS1115 ADC (1619 LSBs)` $ightarrow$ `ESP32 IIR Filter & 128-pt FFT (5.07 Hz Peak)` $ightarrow$ `STA/LTA Trigger (>3.5)` $ightarrow$ `Python UI Red Alert`.

---

## 💰 Budget Options
- **Hackathon MVP:** **₹1,750 INR** (~$21 USD)
- **Production Spec:** **₹9,500 INR** (~$115 USD)
