================================================================================
  MODULE 09: 3D CAD MECHANICAL MODELING & OPENSCAD CHAMBER GENERATOR
================================================================================

Goal: Parametric 3D CAD model generation for 3D printing (STL/FDM/SLA resin) or CNC
      acrylic/aluminum machining.

--------------------------------------------------------------------------------
1. PARAMETRIC CHAMBER DIMENSIONS
--------------------------------------------------------------------------------
- Internal Chamber Volume : V = 350 mL = 350,000 mm^3
- Outer Box Dimensions     : 100 mm (Width) x 100 mm (Length) x 45 mm (Height)
- Wall Thickness           : 4.0 mm
- O-Ring Lid Groove        : 2.5 mm width x 1.8 mm depth (for 2.0 mm silicone O-ring)
- Capillary Needle Hole    : 2.2 mm diameter (press-fit for 27G needle)
- Inlet Barbed Port Hole   : 4.2 mm diameter (M6 thread / press-fit)
- Cable Gland Hole         : 8.5 mm diameter (PG7 thread)
- PCB Mounting Pillars    : 4x M3 standoffs (60 mm x 40 mm hole pattern)

--------------------------------------------------------------------------------
2. OPENSCAD PARAMETRIC SCRIPT (`cad/chamber_3d_model.scad`)
--------------------------------------------------------------------------------
Run `cad/chamber_3d_model.scad` in OpenSCAD (free CAD software) to generate the
3D STL file for 3D printing!

```openscad
// OpenSCAD Parametric Acoustic Chamber Model
// PS ID 26144: Microbarometer Infrasound Sensor

$fn = 100;

// Dimensions (mm)
box_w = 100;
box_l = 100;
box_h = 45;
wall = 4;

module acoustic_chamber() {
    difference() {
        // Outer Main Box
        cube([box_w, box_l, box_h], center=true);
        
        // Inner Cavity (350 mL Volume)
        translate([0, 0, wall/2])
            cube([box_w - 2*wall, box_l - 2*wall, box_h - wall], center=true);
            
        // Hole A: Main Acoustic Inlet Port (4.2mm)
        translate([-box_w/2 + wall/2, 0, 0])
            rotate([0, 90, 0])
                cylinder(r=2.1, h=wall*2, center=true);
                
        // Hole B: Capillary Leak Needle Port (2.2mm)
        translate([box_w/2 - wall/2, 0, 0])
            rotate([0, 90, 0])
                cylinder(r=1.1, h=wall*2, center=true);
                
        // Hole C: Cable Gland PG7 Port (8.5mm)
        translate([0, box_l/2 - wall/2, 0])
            rotate([90, 0, 0])
                cylinder(r=4.25, h=wall*2, center=true);
    }
    
    // PCB Mounting Pillars (4x M3)
    for (x = [-30, 30]) {
        for (y = [-20, 20]) {
            translate([x, y, -box_h/2 + wall + 4])
                difference() {
                    cylinder(r=3.5, h=8, center=true);
                    cylinder(r=1.3, h=10, center=true); // M3 tap hole
                }
        }
    }
}

acoustic_chamber();
```
================================================================================
