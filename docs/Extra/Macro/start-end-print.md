---
layout: default
title: Start Print / End Print
nav_order: 2
parent: Macro
grand_parent: Extra
has_children: true
permalink: /extra/macro/start-end-print/
---

# Esempio di "START_PRINT" ed "END_PRINT" da utilizzare nello Slicer
{: .fw-400 }

## ATTENZIONE: QUESTO E' SOLO UN ESEMPIO NON ANCORA UFFICIALE, NON UTILIZZARLO!!!

All'interno del file `printer.cfg` di Klipper è possibile utilizzare delle Macro per impartire i comandi ad avvio e termine stampa senza effettuare modifiche sullo Slicer, ma semplicemente richiamando questi comandi all'interno dello "Start G-code" ed "End G-code" dello Slicer stesso.

```
# ================================================================================
# GCode Macro: START_PRINT
# Aggiungi START_PRINT nello script di avvio dello Slicer. 
# ================================================================================
[gcode_macro START_PRINT]
gcode:
    G28 ; Home di tutti gli assi    
    BED_MESH_CALIBRATE ; Calibrazione del Bed
    G92 E0 ; Reset dell'estrusore
    G1 Z5.0 F3000 ; Muove l'asse Z un po' in alto per evitare di graffiare il Bed
    G1 X7.1 Y40 Z0.3 F5000.0 ; Spostamento alla posizione iniziale
    G1 X7.1 Y215.0 Z0.3 F1500.0 E15 ; Disegna la prima linea
    G1 X7.4 Y215.0 Z0.3 F5000.0 ; Spostamento laterale
    G1 X7.4 Y40 Z0.3 F1500.0 E30 ; Disegna la seconda linea
    G92 E0 ; Reset dell'estrusore
    G1 Z5.0 F3000 ; Muove l'asse Z un po' in alto per evitare di graffiare il Bed

# ================================================================================
# GCode Macro: END_PRINT
# Aggiungi END_PRINT nello script di fine dello Slicer. 
# ================================================================================
[gcode_macro END_PRINT]
gcode:
    G1 Y190 F1500; Sposta Y davanti
    G10 ; Imposta l'offset?  O ritrae?
    G91 ; Posizionamento relativo
    G1 Z+10 ; Muove Z in alto per non colpire nulla
    G1 E-10 F300 ; Ritrae -10
    G90 ; Posizionamento assoluto
    G1 X10 Y220 F2000 ; Muove X10, Y220
    M104 S0 ; Spegne l'estrusore (lo imposta a 0)
    M140 S0 ; Spegne il Bed (lo imposta a 0)
    M106 S0 ; Spegne le ventole di raffreddamento
    M84 ; Disabilita gli stepper motors
```
