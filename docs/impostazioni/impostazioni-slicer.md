---
layout: default
title: Impostazioni Slicer
parent: Impostazioni
nav_order: 2
permalink: /impostazioni-slicer/
---

{% include breadcrumbs.html %}

## IMPOSTAZIONI SLICER

Per l'upload diretto su server con Prusaslicer/Superslicer basta inserie l'IP del server come di seguito:
<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image13.png" height="350">
</p>

Mentre con Ultimaker Cura è necessario installare dal Marketplace il Plugin "OctoPrint Connection"

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/octoprint_connection.png" height="100">
</p>

una volta installato chiudere e riaprire Ultimaker Cura e andare su "Preferences --> Configure Cura..." selezionare "Printers" nel menu a sx, selezionare la propria stampante e infine cliccare su "Connect OctoPrint"

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/connect_octoprint.png" height="50">
</p>

cliccare su "Add" ed inserire un nome, il proprio IP di Moonraker e la porta e cliccare su OK

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/add_moonraker.png" height="200">
</p>

una volta aggiunta l'istanza, inserire una API Key casuale (es: 1234567890) e cliccare su Connect

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/moonraker_octoprint_cura.png" height="300">
</p>

se tutti i passi sono stati effettuati correttamente ci si connetterà senza problemi a Moonraker e si potranno inviare i file direttamente dallo Slicer all'interfaccia Web. 


Ricordarsi di disabilitare: controllo accelerazione, coasting, extra restart distance e advance extruder pressure..

Per approfondimenti vai [QUI](https://github.com/KevinOConnor/klipper/blob/master/docs/Slicers.md)
