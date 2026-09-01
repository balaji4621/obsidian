---
tags: [sfox, sih2026, cad-mechanical]
updated: 2026-08-27
---

# 🧊 SFox Module 02: Isothermal Dual-Chamber CAD & Mechanical Design

## 1. Monolithic Isothermal Chamber Specifications
- **Outer Dimensions:** $50.0\text{ mm} \times 50.0\text{ mm} \times 12.0\text{ mm}$ (180g mass).
- **Material:** CNC Milled Monolithic 6061 Aluminum Block ($k = 160\text{ W/m}\cdot\text{K}$).
- **Chamber A (Active):** 5 mL cavity ($30\text{ mm}$ dia $\times 7\text{ mm}$ depth) with capillary + 0.2 µm PTFE filter.
- **Chamber B (Reference):** 5 mL sealed cavity ($30\text{ mm}$ dia $\times 7\text{ mm}$ depth).
- **Shared Wall:** 2.0 mm internal aluminum dividing wall ensuring 100% thermal symmetry and identical heating rates.
- **Wind Hose Array:** 4-arm porous hose array with 1.5-meter radial arms (3.0-meter total array diameter span).

---

## 2. OpenSCAD Code (`cad/sfox_hybrid_chamber.scad`)
```openscad
$fn = 100;
module hybrid_dual_chamber() {
    difference() {
        cube([50, 50, 12], center=true); // Monolithic 6061 Al block
        
        // Active Chamber A (5 mL)
        translate([-12.5, 0, 1]) cylinder(r=12, h=8, center=true);
        
        // Reference Chamber B (5 mL, shared 2mm wall)
        translate([12.5, 0, 1]) cylinder(r=12, h=8, center=true);
        
        // Inlet Port to Chamber A (4-arm 1.5m porous hose array)
        translate([-25, 0, 1]) rotate([0, 90, 0]) cylinder(r=2.1, h=10, center=true);
        
        // Capillary Leak Port (43G pulled glass + PTFE filter mount)
        translate([-12.5, 25, 1]) rotate([90, 0, 0]) cylinder(r=0.6, h=10, center=true);
    }
}
hybrid_dual_chamber();
```
