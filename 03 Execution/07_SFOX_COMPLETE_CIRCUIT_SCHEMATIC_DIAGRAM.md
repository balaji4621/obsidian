---
tags: [sfox, sih2026, circuit-schematic]
updated: 2026-08-27
---

# ⚡ SFox Module 07: Complete Circuit Schematic Diagram

## 1. System Block Diagram & Dual Sensor Architecture

```
  +-----------------------+      +-------------------------+
  |  CHAMBER A (ACTIVE)   |      | CHAMBER B (REF 6061 Al) |
  |  5 mL Monolithic Al   |      |  5 mL Monolithic Al     |
  |  [43G Glass + PTFE]   |      |   (Shared 2mm Divider)  |
  +-----------+-----------+      +------------+------------+
              |                               |
    [MPXV7002DP Sensor Vin+]        [MPXV7002DP Sensor Vin-]
    (Acoustic Wave + Drift)          (Common-Mode Drift Only)
              |                               |
              | Vin+ (Pin 3)                  | Vin- (Pin 2)
              +---------------+---------------+
                              |
                              v
             +---------------------------------+
             |     INA128PA INSTRUMENTATION    | <--- Rg = 499 Ω (0.1%) [Pins 1 & 8]
             |      AMPLIFIER (Gain = 101.2x)  | <--- Driven Guard Ring @ Vref (1.65V)
             +----------------+----------------+
                              | Vout1 (Pin 6)
                              v
             +---------------------------------+
             |   OPA2188 4TH-ORDER SALLEN-KEY  | <--- Low-Pass Filter (fc = 20.0 Hz)
             |      BUTTERWORTH 20Hz LPF       | <--- Kills 50Hz Mains Hum (-32 dB)
             +----------------+----------------+
                              | Vout_filtered
                              v
             +---------------------------------+
             |    ADS1256 24-BIT SPI ADC       | <--- Vref = 2.500V (REF5025)
             |   (100 SPS, 0.298 uV/bit Res)   | <--- AIN0 = Signal, AIN1 = Vref (1.65V)
             +----------------+----------------+
                              | SPI Bus (SCLK, DIN, DOUT, CS, DRDY)
                              v
             +---------------------------------+
             |     ESP32-S3-WROOM-1 MCU        | <--- Dual-Core 240MHz + Hardware FPU
             |  (512-pt FFT & TinyML AI Core)  | <--- Sutherland's Engine & MAC TDOA Sync
             +---------------------------------+
```

---

## 2. Interactive SVG & HTML Circuit Viewers
- Interactive Web Schematic: `sfox_circuit_viewer.html`
- Vector Graphic File: `sfox_full_circuit_schematic.svg`
