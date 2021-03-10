---
layout: default
title: Start Print ed End Print
nav_order: 9
parent: Esempi di Macro su Klipper
has_children: false
permalink: /start-end-print/
---

# ================================================================================
# GCode Macro: START_PRINT
# Add START_PRINT in your slicers starting script. 
# ================================================================================
[gcode_macro START_PRINT]
gcode:
    G28; Home all axes    
    BED_MESH_CALIBRATE    
    G92 E0; Reset Extruder
    G1 Z5.0 F3000; Move Z Axis up little to prevent scratching of Heat Bed
    G1 X7.1 Y40 Z0.3 F5000.0; Move to start position #Y20
    G1 X7.1 Y215.0 Z0.3 F1500.0 E15; Draw the first line
    G1 X7.4 Y215.0 Z0.3 F5000.0; Move to side a little
    G1 X7.4 Y40 Z0.3 F1500.0 E30; Draw the second line #Y20
    G92 E0; Reset Extruder
    G1 Z5.0 F3000; Move Z Axis up little to prevent scratching of Heat Bed

# ================================================================================
# GCode Macro: END_PRINT
# Add END_PRINT in your slicers ending script
# ================================================================================
[gcode_macro END_PRINT]
gcode:
    G1 Y190 F1500; bring Y up front 
    G10 ; set tool offset?  or retract?
    G91; Relative Positioning
    G1 Z+10; Move Z up so it doesn't hit anything
    G1 E-10 F300; Retrack-10
    G90; Absolute Positioning
    G1 X10 Y220 F2000; Move to X10, Y220
    M104 S0; Turn off Extrude (set it to 0)
    M140 S0; Turn off Bed (set it to 0)
    M106 S0; turn off cooling fan
    M84; Disable steppers
