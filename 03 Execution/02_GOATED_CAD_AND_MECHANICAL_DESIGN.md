================================================================================
  MODULE 02: SLA 3D-PRINTED HYBRID CHAMBER CAD & MECHANICAL DESIGN
================================================================================

1. HYBRID CHAMBER DIMENSIONS
- Outer Footprint  : 50.0 mm x 50.0 mm x 12.0 mm
- Chamber A Volume : 5 mL cavity (30 mm diameter x 7 mm height)
- Chamber B Volume : 5 mL cavity (30 mm diameter x 7 mm height)
- Capillary Mount  : 2.2 mm press-fit hole for 27G needle (30mm length)
- Inlet Barb       : M6 thread / 4mm barbed fitting
- Material         : Tough SLA Photopolymer Resin (0.05mm layer precision)

2. OPENSCAD SCRIPT (`cad/goated_hybrid_chamber.scad`)
```openscad
$fn = 100;
module hybrid_dual_chamber() {
    difference() {
        cube([50, 50, 12], center=true);
        // Chamber A (Active)
        translate([-12, 0, 1]) cylinder(r=12, h=8, center=true);
        // Chamber B (Sealed Ref)
        translate([12, 0, 1]) cylinder(r=12, h=8, center=true);
        // Inlet Port to Chamber A
        translate([-25, 0, 1]) rotate([0, 90, 0]) cylinder(r=2.1, h=10, center=true);
        // Capillary Port to Chamber A
        translate([-12, 25, 1]) rotate([90, 0, 0]) cylinder(r=1.1, h=10, center=true);
    }
}
hybrid_dual_chamber();
```
================================================================================
