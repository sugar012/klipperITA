---
layout: default
title: Impostazioni Cura per utilizzo con Klipper
parent: Extra
nav_order: 6
has_children: false
permalink: /extra/cura-klipper/
---

# Cura slicer & Klipper
{: .fw-400 }

Link al post di [Alberto Zanardo @alb_za](https://t.me/Klipper3DITA/72760 "Utilizzo Cura & Klipper"){:target="_blank"}

Usare Cura con flavor "*Marlin*".

# IMPOSTARE L'UPLOAD DI GCODE CON THUMBNAIL
* Scaricare e copiare il plugin *Cura2Moonraker* nella cartella plugin di Cura (seguire la guida riportata su GitHub [Cura2MoonrakerPlugin](https://github.com/emtrax-ltd/Cura2MoonrakerPlugin "Cura2MoonrakerPlugin"){:target="_blank"}
* aprire Cura, *Preferences>Configure Cura>Printers*, selezionare la propria stampante e cliccare su *"Connect Moonraker"*. Se il pulsante non è presente, è stato installato male il plugin oppure non avete riavviato Cura
* impostare il *"Moonraker Address"* con il proprio IP della stampante (nel mio caso `http://192.168.1.8/`) e cliccare su *"Save config"*
* a questo punto dovrebbe comparire l'opzione *"Upload to `<nome stampante>`"* dopo lo slicing in basso a destra

# SOLO THUMBNAIL
Se serve solo il thumbnail oppure il metodo precedente non ha funzionato:
* aprire Cura
* *Extensions>Post processing>Modify G-Code>Add a script*
* aggiungere *"Create thumbnail"* e settare la risoluzione (300x300 va bene per Fluidd)
* per cambiare il colore dell'oggetto, cambiare il colore del materiale in uso

# UTILIZZARE VARIABILI NELLO START_GCODE
Trovate tutte le variabili di Cura in *C:\Program Files\Ultimaker Cura 4.11.0\resources\definitions* dentro il file *fdmprinter.def.json*
Due variabili comode da mettere nello Start G-Code sono *{material_initial_print_temperature}* e *{material_bed_temperature}*. Sì, serve usare le parentesi graffe altrimenti non funzionano.
Quindi su Cura il mio Start G-Code è **"START_PRINT EXTRUDER_TEMP={material_initial_print_temperature} BED_TEMP={material_bed_temperature}"**.
E nella mia macro di Klipper sono presenti *EXTRUDER_TEMP* e *BED_TEMP* in questo modo *"M140 S{BED_TEMP} M109 S{EXTRUDER_TEMP}"*

# ATTIVARE FIRMWARE RETRACTION
* aprire Cura
* cliccare su *"marketplace"* in altro a destra
* nella scheda *"plugins"* scendere e installare il plugin *"printer settings"* sono in ordine alfabetico
* riavviare Cura
* se non c'è già la scheda *"Printer settings"* nella barra di destra (assieme a quality, walls, top/bottom...) aggiungerla cliccando sull'hamburger menu affianco alla barra di ricerca e spuntare la Firmware retraction per visualizzarla sulla side bar.
