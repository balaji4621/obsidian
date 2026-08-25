================================================================================
  MODULE 08: GROUND-UP SCHEMATIC & PCB LAYOUT GUIDE (KICAD / EASYEDA)
================================================================================

Goal: Complete schematic netlist, 2-layer PCB layout rules, trace widths, and star
      ground plane design for custom board fabrication (JLCPCB / PCBWay).

--------------------------------------------------------------------------------
1. PCB SPECIFICATIONS
--------------------------------------------------------------------------------
- Dimensions    : 80 mm x 60 mm (Double-Sided FR4, 1.6 mm thickness, 1 oz Cu).
- Layer Stackup : Top Layer = Signal Traces + Power Vcc Rails.
                  Bottom Layer = Continuous Ground Plane (GND).
- Minimum Trace : 10 mil (0.25 mm) for signals, 25 mil (0.63 mm) for power rails.
- Via Size      : 24 mil hole / 40 mil diameter.

--------------------------------------------------------------------------------
2. SCHEMATIC NETLIST TABLE (PIN CONNECTIONS)
--------------------------------------------------------------------------------

  Component 1            Pin        Connected To Component 2       Pin      Signal Name
  ---------------------------------------------------------------------------------------
  Sensor (MPXV7002DP)    1 (Vout)   INA128 InAmp                  3 (Vin+)  SIG_POS
  Sensor (MPXV7002DP)    2 (GND)    System Ground Plane           GND      GND
  Sensor (MPXV7002DP)    3 (Vcc)    HT7333 LDO Output             +3.3V    AVCC
  Sensor (MPXV7002DP)    4 (Vref)   INA128 InAmp                  2 (Vin-)  SIG_NEG

  INA128 InAmp           1 (Rg1)    Rg Resistor (499 ohm 0.1%)    1        RG1
  INA128 InAmp           8 (Rg2)    Rg Resistor (499 ohm 0.1%)    2        RG2
  INA128 InAmp           5 (Ref)    OPA2188 Buffer Output         1        VREF_1.65V
  INA128 InAmp           6 (Vout)   OPA2188 LPF Stage 1 Input     3 (IN+)  STAGE1_IN
  INA128 InAmp           7 (V+)     HT7333 LDO Output             +3.3V    AVCC
  INA128 InAmp           4 (V-)     System Ground Plane           GND      GND

  OPA2188 OpAmp Unit 1   1 (Out1)   INA128 Ref & LPF Ref          5, Ref   VREF_1.65V
  OPA2188 OpAmp Unit 1   2 (IN1-)   OPA2188 Unit 1 Out1           1        VREF_1.65V
  OPA2188 OpAmp Unit 1   3 (IN1+)   Resistor Divider (10k/10k)    Midpoint VDIV_1.65V

  OPA2188 OpAmp Unit 2   7 (Out2)   ADS1115 ADC Channel           A0       AFE_OUT_CLEAN

  ADS1115 ADC            1 (VDD)    HT7333 LDO Output             +3.3V    AVCC
  ADS1115 ADC            2 (GND)    System Ground Plane           GND      GND
  ADS1115 ADC            3 (SCL)    ESP32-S3 GPIO 22              22       I2C_SCL
  ADS1115 ADC            4 (SDA)    ESP32-S3 GPIO 21              21       I2C_SDA
  ADS1115 ADC            5 (ADDR)   System Ground Plane           GND      I2C_ADDR_GND

--------------------------------------------------------------------------------
3. PCB LAYOUT & EMI GROUNDING RULES
--------------------------------------------------------------------------------
1. STAR GROUNDING: Separate Analog Ground (AGND) under INA128/OPA2188 from Digital
   Ground (DGND) under ESP32. Join them at a SINGLE point right near the LDO GND pin!
2. DECOUPLING: Place 100nF ceramic capacitor within 3mm of EVERY IC Vcc pin!
3. GUARD RINGS: Surround INA128 input traces (Pins 2 & 3) with a grounded guard trace
   to prevent PCB leakage currents.
================================================================================
