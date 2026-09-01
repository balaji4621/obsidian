---
tags: [sfox, sih2026, workflow]
updated: 2026-08-26
---

# 🏆 SFox SIH 2026 Master Execution Workflow
**Project:** SFox Hybrid Coin-Sized TinyML Microbarometer Infrasound Sensor  
**Sponsoring Agency:** National Technical Research Organisation (NTRO) | **PS ID:** 26144  

---

## 🗓️ 6-Phase Execution Path

```
  [ PHASE 0 ] ──► Software Environment & Toolchain Setup (2 Hours)
  [ PHASE 1 ] ──► BOM Procurement & JLCPCB Order (1 Hour)
  [ PHASE 2 ] ──► 3D SLA Chamber A & 6061 Al Chamber B Machining (4 Hours)
  [ PHASE 3 ] ──► Circuit Design, AFE 4-Layer PCB Assembly & Calibration (6 Hours)
  [ PHASE 4 ] ──► ESP32 Firmware, Sutherland's Engine & TinyML AI (6 Hours)
  [ PHASE 5 ] ──► 6 Mandatory Validation Tests & Proof Pack (4 Hours)
  [ PHASE 6 ] ──► 3-Minute Stage Pitch Script & Jury Defense (Hackathon Day)
```

---

## 🚀 Key Innovations
1. **ESP-NOW Swarm TDOA Mesh:** Triangulates explosion origin coordinates $(\hat{x}, \hat{y})$ within $\pm 5\text{m}$ across a $5\text{ km}$ grid.
2. **Acoustic BIST Auto-Diagnostic:** Micro-piezo ping verifies capillary leak health every 24 hours. If $\tau > 15\text{s}$, a 50 mW PTC micro-heater fires to clear condensation.
3. **Solar Energy Harvester:** BQ25570 MPPT harvester + 50x50mm solar panel for continuous 24/7 deployment.
4. **Closed-Loop Force-Balance Upgrade:** Next-gen capacitive diaphragm + PID electrostatic force feedback for $2.7\text{ mHz} - 200\text{ Hz}$ response with $>155\text{ dB}$ dynamic range.
