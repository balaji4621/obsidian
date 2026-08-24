# 📡 EXECUTIVE STRATEGIC & TECHNICAL EXECUTION PLAN
**Project:** Indigenous High-Sensitivity Microbarometer Infrasound Sensor  
**Sponsoring Agency:** National Technical Research Organisation (NTRO) | **PS ID:** 26144  
**Target Domain:** Sub-20 Hz Strategic Infrasound Surveillance & Early Disaster Warning  

---

## PHASE 1: THE ARCHITECTURAL BLUEPRINT

### 1. System Context Diagram
```
===================================================================================================
                                      SYSTEM CONTEXT DIAGRAM
===================================================================================================

 [ ATMOSPHERIC INPUTS ]
   ├─ Infrasound Pressure Waves (0.01 - 20 Hz, 0.01 to 10 Pa) ──► [ Layer 1: Porous Hose Array ]
   └─ Turbulent Wind Eddies (0.1 - 5 Hz, 20 to 50 Pa Noise) ────► (Rejects Incoherent Wind >20 dB)
                                                                          │
                                                                   [ Coherent Wave ]
                                                                          │
                                                                          ▼
 [ MECHANICAL ACOUSTIC CORE ]                                     [ Layer 2: 350 mL Chamber ]
   ├─ Weather Static Pressure Shifts (<0.001 Hz) ───────────────► (Equalizes via 0.288mm Capillary)
   └─ Sub-20 Hz Infrasound AC Fluctuations ─────────────────────► (Flexes MPXV7002DP Diaphragm)
                                                                          │
                                                                 [ 1.0 mV/Pa Analog ]
                                                                          │
                                                                          ▼
 [ ANALOG FRONT-END (AFE) ]                                       [ Layer 3: INA128 + OPA2188 ]
   ├─ INA128 Instrumentation Amplifier (Rg=499Ω, Gain=101.2x) ─► Boosts Signal to 101.2 mV AC
   ├─ OPA2188 Mid-Supply Reference Generator ───────────────────► Biases Output to 1.65V DC
   └─ OPA2188 4th-Order Sallen-Key LPF (Fc=20 Hz) ──────────────► Attenuates Mains (50Hz -18dB)
                                                                          │
                                                               [ 1.65V ± 0.1V Clean Analog ]
                                                                          │
                                                                          ▼
 [ EMBEDDED & DSP ENGINE ]                                       [ Layer 4: ADS1115 + ESP32-S3 ]
   ├─ 16-bit ADS1115 ADC (I2C @ 400kHz, 100 SPS Hardware Loop) ─► Digitizes to 1619 LSBs
   ├─ Single-Pole IIR Filter (alpha=0.995, Fc=0.05 Hz) ─────────► Removes Residual DC Offset
   ├─ Sutherland's Law Thermal Engine (mu(T) Tracking) ────────► Compensates Capillary Corner
   ├─ 128-Point Real-Time FFT & 4-Spectrum Welch Averaging ────► Provides +6 dB SNR Boost
   └─ STA/LTA Event Classifier (Trigger Ratio > 3.5) ───────────► Detects Transients < 100 ms
                                                                          │
                                                             [ JSON Packets via WebSocket/Serial ]
                                                                          │
                                                                          ▼
 [ DASHBOARD & TELEMETRY ]                                       [ Layer 5: Python UI / SD Log ]
   ├─ Local Storage (MicroSD Card, Ring Buffer 48B/sample) ────► 100% Offline Data Resilience
   ├─ Python Live Telemetry UI (PyQtGraph / Matplotlib) ────────► Real-Time Waterfall Heatmap
   └─ Alarm Dispatcher (Visual Alert & Event Log) ─────────────► Event Classification & Audit
===================================================================================================
```

### 2. Tech Stack & Materials Specification
- **Acoustic Chamber:** 350 mL Acrylic / PVC Box ($V=3.5	imes 10^{-4}	ext{ m}^3$, $4	ext{ mm}$ wall thickness, $C_a = 2.47	imes 10^{-9}	ext{ m}^3/	ext{Pa}$).
- **Capillary Leak:** 27G Stainless Steel Needle ($d=0.288	ext{ mm ID}, L=30.0	ext{ mm} ightarrow R_a = 3.225	imes 10^9	ext{ Pa}\cdot	ext{s/m}^3, f_c = 0.020	ext{ Hz}, 	au = 8.0	ext{s}$).
- **Transducer:** NXP MPXV7002DP Differential Pressure Sensor ($\pm 2.0	ext{ kPa}$ range, $1.0	ext{ mV/Pa}$).
- **InAmp:** TI INA128 ($8	ext{ nV}/\sqrt{	ext{Hz}}$ noise, $100	ext{ dB}$ CMRR, $R_g=499\ \Omega ightarrow 	ext{Gain}=101.2	ext{x}$).
- **Op-Amps:** TI OPA2188 Zero-Drift Dual Op-Amp (auto-zero chopping eliminates 1/f noise down to $0.01	ext{ Hz}$).
- **Anti-Alias LPF:** 4th-Order Sallen-Key Butterworth ($f_c = 20	ext{ Hz}$, $R=11.3	ext{k}\Omega, C_1=C_3=1.0\mu	ext{F}, C_2=390	ext{nF}, C_4=100	ext{nF}$).
- **ADC & Microcontroller:** ADS1115 ($16	ext{-bit}, 250	ext{ SPS}$) + ESP32-S3 ($240	ext{ MHz}$, hardware FPU).
- **Power Management:** HT7333 / TPS7A4700 LDO + $3.7	ext{V } 3000	ext{ mAh}$ Li-Po battery. Disabling OLED drops power to $<45	ext{ mW}$ ($>180	ext{ hours}$ runtime).

---

## PHASE 2: CRITICAL PATH ROADMAP (0 TO 1)
- **Sprint 1 (Weeks 1-2):** Mechanical Chamber, Capillary Leak Calibration ($	au = 8.0	ext{s}$) & Porous Hose Array ($>20	ext{ dB}$ wind rejection).
- **Sprint 2 (Weeks 3-4):** Low-Noise AFE Circuitry (INA128 + OPA2188 20Hz LPF + 1.65V Vref buffer).
- **Sprint 3 (Weeks 5-6):** 100 Hz Timer Firmware, ADS1115 ADC Driver, DC Removal Filter & STA/LTA Trigger.
- **Sprint 4 (Weeks 7-8):** Python Waterfall UI, Field Calibration Tests, Packaging & 3-Minute Pitch Rehearsal.

---

## PHASE 3: RESOURCE & BUDGET ALLOCATION
- **Category A (Mechanical MVP):** ₹1,280 INR ($15.45 USD)
- **Category B (Electronics & Signal Chain):** ₹2,100 INR ($25.25 USD)
- **Category C (Enclosure & Test Props):** ₹520 INR ($6.25 USD)
- **Total Hackathon MVP Cost:** **₹3,900 INR** (~$47.00 USD) (Minimal Tower: **₹1,900 INR**)

---

## PHASE 4: PRE-MORTEM & CONTINGENCY PROTOCOL
1. **FM-1 Capillary Clogging:** Hydrophobic PTFE membrane ($0.45\mu	ext{m}$) + $50	ext{ mW}$ PTC heater coil.
2. **FM-2 50 Hz Mains Aliasing:** 4th-order Sallen-Key 20Hz LPF + aluminum foil shielding + digital 50 Hz notch filter.
3. **FM-3 Parasitic Tubing Compliance:** Direct-mount MPXV7002DP to chamber with rigid M10 brass fitting.
4. **FM-4 Wind Storm False Alarms:** 1.5m arm porous hose array + buried gravel installation + spectral ratio validation.
