---
tags: [dashboard, sih2026, sfox-hybrid]
updated: 2026-08-26
---

# 🦊 SFox Hybrid Infrasound Master Workspace

> [!success] **SELECTED TARGET PROJECT:** [[SFox Hybrid Infrasound Master Plan]]
> **PS ID 26144 (NTRO)** — World's first $50\times 50\text{ mm}$ Coin-Sized TinyML Microbarometer Sensor. Budget: **₹1,900 MVP** | **₹3,650 Prototype** | **₹3,860 Industrial Batch**.

---

## 🗺️ Master Project Navigation

### 🟢 [[01 Projects]] — Core System & Workflow
- **[[SFox Hybrid Infrasound Master Plan]]** — Complete Master Architecture, Transducer Specs & Benchmarks.
- **[[SFox Full Project Workflow]]** — Phase 0 to Phase 6 Top-to-Bottom Execution Guide.
- **[[SFox Executive Summary One-Pager]]** — Judges' Leave-Behind Document.
- **[[SFox Presentation Slide Deck & Jury Defense]]** — 12-Slide Pitch Deck, Stage Script & Top 25 Jury Q&A Defenses.
- **[[SIH 2026 Cracking Strategy & Master Guide]]** — SIH 2026 Judging Matrix & 10/10 Winning Strategy.

---

### 🟣 [[03 Execution]] — Blueprint & Execution Modules
- **[[00_SFOX_MASTER_BLUEPRINT]]** — Executive Summary, Signal Flow Matrix & Budget.
- **[[01_SFOX_PHYSICS_AND_MATH]]** — Kirchhoff-Love Mechanics, Hagen-Poiseuille $R_a$, $C_a$, $f_c=0.020\text{ Hz}$, Brownian Noise & Sutherland's Law $\mu(T)$.
- **[[02_SFOX_CAD_AND_MECHANICAL_DESIGN]]** — Monolithic Isothermal 6061 Aluminum Dual Chamber OpenSCAD Model Script.
- **[[03_SFOX_CIRCUIT_AND_PCB_KICAD]]** — 4-Layer ENIG PCB Layout, Driven Guard Rings, Faraday Shield Can & Component Netlist.
- **[[04_SFOX_FIRMWARE_TINYML_DSP]]** — ESP32-S3 Firmware Code, 512-pt Sliding FFT, BIST Auto-Diagnostic Engine & TFLite 1D-CNN Model.
- **[[05_SFOX_TESTING_PROOF_AND_PITCH]]** — Real-World $N=1,420$ Test Set Evaluation, 6 Mandatory Tests & Stage Pitch Script.
- **[[06_SFOX_COMPLETE_PROCUREMENT_ORDER_LIST]]** — Verified JLCPCB SMT Order & Off-the-Shelf Procurement Breakdown.
- **[[07_SFOX_COMPLETE_CIRCUIT_SCHEMATIC_DIAGRAM]]** — Full Hardware Pin-by-Pin Circuit Schematic Diagram.

---

## 📊 Quick Specification Benchmark

| Parameter | SFox Production Module | Commercial Imports (Chaparral 64Vx2) |
|---|---|---|
| **Unit Production Cost** | **₹3,650 Prototype / ₹3,860 Industrial** | ₹4,50,000+ ($5,400 USD) |
| **Form Factor & Mass** | **180g (50x50mm Coin Module)** | 3.2 kg (Bulky jar) |
| **Passband & Cutoff** | **0.020 Hz – 20.0 Hz (17.6um Capillary)** | 0.01 Hz – 50 Hz |
| **Thermal Cancellation** | **>97% Rejection (Monolithic Al Bridge)** | Manual compensation |
| **Power Consumption** | **<45 mW (>180 Hours Li-Po)** | 1.2 W (Bulky solar required) |
| **Edge AI** | **On-Device 94.6% TinyML AI (<8.5ms)** | None (Raw analog streaming only) |
| **Self-Test** | **24h Automated BIST + PTC Heater** | Manual lab calibration |
| **Swarm Triangulation** | **ESP-NOW MAC Timer Sync (±5m target)** | Proprietary / Expensive add-on |
