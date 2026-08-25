================================================================================
  MODULE 03: 2-LAYER JLCPCB SCHEMATIC & STAR GROUNDING GUIDE
================================================================================

1. PCB SPECIFICATIONS
- Board Size : 50.0 mm x 50.0 mm (Double-Sided FR4, 1.6mm thickness, 1 oz Cu).
- Layer 1 (Top)    : Signal traces + Power rails + SLA Chamber mounting pad.
- Layer 2 (Bottom) : Continuous Star Ground Plane (AGND & DGND split).

2. KEY COMPONENT NETLIST
- U1: INA128PA (Instrumentation Amp, Gain=101.2x, Rg=499 ohm 0.1%).
- U2: OPA2188AIDR (Dual Zero-Drift Op-Amp, 1.65V Vref buffer + 20Hz 4th-order LPF).
- U3: ADS1256IDBR (24-bit SPI ADC) or ADS1115 (16-bit I2C ADC).
- U4: ESP32-S3-WROOM-1 Microcontroller.
- U5: TPS7A4700 / HT7333 Low-Noise LDO Regulator (3.3V / 5.0V).

3. KICAD / EASYEDA BOM (`kicad/goated_bom.csv`)
================================================================================
