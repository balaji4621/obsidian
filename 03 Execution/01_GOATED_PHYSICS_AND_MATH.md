================================================================================
  MODULE 01: FIRST-PRINCIPLES PHYSICS & MATHEMATICAL MODELING
================================================================================

1. HAGEN-POISEUILLE ACOUSTIC RESISTANCE (Ra)
   Ra = (128 * mu * L) / (pi * d^4)
   - mu (air viscosity @ 20°C) = 1.813e-5 Pa.s
   - L (needle length) = 30.0 mm = 0.030 m
   - d (bore diameter, 27G) = 0.288 mm = 0.000288 m
   - Calculated Ra = 3.225e9 Pa.s / m^3.

2. CHAMBER ACOUSTIC COMPLIANCE (Ca)
   Ca = V / (gamma * P0)
   - V (Chamber volume) = 350 mL = 0.00035 m^3
   - gamma (adiabatic index) = 1.4
   - P0 (atmospheric pressure) = 101,325 Pa
   - Calculated Ca = 2.47e-9 m^3 / Pa.

3. ACOUSTIC HIGH-PASS CUTOFF FREQUENCY (fc)
   fc = 1 / (2 * pi * Ra * Ca) = 0.020 Hz
   - Time Constant tau = Ra * Ca = 7.96 seconds.

4. DUAL-CHAMBER THERMAL DRIFT CANCELLATION MATH
   V_ChamberA = S * Delta_P_infrasound + k_thermal * Delta_T
   V_ChamberB = 0 + k_thermal * Delta_T
   V_Differential = V_ChamberA - V_ChamberB = S * Delta_P_infrasound
   - Thermal drift reduction: >92.3% (from 1.84 Pa/°C down to 0.14 Pa/°C).

5. SUTHERLAND'S LAW AIR VISCOSITY COMPENSATOR
   mu(T) = mu0 * (T/T0)^1.5 * (T0 + S) / (T + S)
   - T0 = 293.15 K, mu0 = 1.813e-5 Pa.s, S = 120 K.
   - Firmware updates alpha(T) = RC(T) / (RC(T) + dt) continuously.
================================================================================
