================================================================================
  MODULE 10: TRANSDUCTION PHYSICS & PRINCIPLE SELECTION MATRIX
================================================================================

Goal: Select and understand the exact physical principle for your custom ground-up
      infrasound transducer.

--------------------------------------------------------------------------------
1. THE 4 GROUND-UP TRANSDUCTION PRINCIPLES
--------------------------------------------------------------------------------

PRINCIPLE A: DIFFERENTIAL CAPACITIVE DIAPHRAGM
- Physics: $C = \frac{\varepsilon_0 \varepsilon_r A}{d_0 - w(P)}$
- Mechanism: A flexible metalized Kapton/Aluminum diaphragm sits $50-100\ \mu\text{m}$
  above a fixed PCB copper electrode. Pressure $\Delta P$ flexes the diaphragm,
  changing gap $d_0$, causing capacitance $C$ to shift.
- Sensitivity: High ($10 - 50\text{ pF/Pa}$).
- Readout IC: Capacitance-to-Digital Converter (AD7745 / AD7746).
- Pros: Extremely low mechanical hysteresis, zero DC friction.
- Cons: Requires cleanroom/precision spacer assembly ($100\ \mu\text{m}$ gap).

PRINCIPLE B: WHEATSTONE PIEZORESISTIVE MEMBRANE
- Physics: $\frac{\Delta R}{R_0} = G \cdot \varepsilon(P)$
- Mechanism: Conductive carbon-nanotube (CNT) or silicon strain gauges are bonded
  to a $0.2\text{ mm}$ silicone/polyimide diaphragm in a Wheatstone bridge.
- Sensitivity: $1.0\text{ mV/V/Pa}$.
- Readout IC: INA128 Instrumentation Amp + ADS1115/ADS1256 ADC.
- Pros: Simple Wheatstone circuit, highly rugged, easy to build without cleanroom.
- Cons: Minor temperature expansion (cancelled by bridge).

PRINCIPLE C: OPTICAL REFLECTIVE DISPLACEMENT (INFRARED)
- Physics: $I_{\text{photo}} \propto \frac{1}{[d_0 + w(P)]^2}$
- Mechanism: An IR LED shines onto a reflective silver diaphragm. A phototransistor
  (QRE1113 / TCRT5000) measures reflected light intensity as diaphragm moves.
- Sensitivity: $5.0\text{ mV/Pa}$.
- Readout Op-Amp: Transimpedance amplifier (TIA) using OPA2188.
- Pros: 100% ELECTRICAL ISOLATION! Zero electrical connection to diaphragm.
- Cons: Sensitive to ambient light leaks (requires light-tight black chamber).

PRINCIPLE D: INTEGRATED DIFFERENTIAL SILICON PIEZORESISTIVE (MPXV7002DP)
- Physics: On-chip micromachined silicon piezoresistors + internal temperature trim.
- Readout: $1.0\text{ mV/Pa}$ analog voltage out.
- Pros: 100% reliable, zero fabrication defect risk during hackathon.

--------------------------------------------------------------------------------
2. SELECTION RECOMMENDATION
--------------------------------------------------------------------------------
- FOR HACKATHON MVP / PROTOTYPE : Choose **Principle D (MPXV7002DP)** or **Principle B (Silicone Piezoresistive)**.
- FOR PRODUCTION / DEFENSE RESEARCH: Choose **Principle A (Capacitive Kapton + AD7745)**.
================================================================================
