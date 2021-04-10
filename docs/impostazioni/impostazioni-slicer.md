---
layout: default
title: Impostazioni Slicer
parent: Impostazioni
nav_order: 2
permalink: /impostazioni/impostazioni-slicer/
---

# Impostazioni Slicer
{: .fw-400 }


**ATTENZIONE: Prima di procedere è necessario accertarsi che sia stata configurata la stringa {% raw %}`[octoprint_compat]`{% endraw %} all'interno del file di configurazione `moonraker.conf`, in caso non sia stata configurata, la seguente procedura non funzionerà.**


### PRUSASLICER/SUPERSLICER

Per l'upload diretto su server con Prusaslicer/Superslicer basta inserie l'IP e la porta del server moonraker nel formato `<IP>:<PORTA>` come da seguente esempio:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image13.png" height="350">
</p>

una volta premuto `OK` se tutti i passi sono stati effettuati correttamente ci si connetterà senza problemi a Moonraker e si potranno inviare i file direttamente dallo Slicer all'interfaccia Web. 

Ricordarsi di disabilitare: controllo accelerazione, coasting, extra restart distance e advance extruder pressure...

Per approfondimenti vai [QUI](https://github.com/KevinOConnor/klipper/blob/master/docs/Slicers.md){:target="_blank"}

- **Configurazione Opzionale per visualizzazione layer di stampa**

In caso si volesse visualizzare il numero di layer da interfaccia web (Fluidd o Mainsail) basta andare su Prusaslicer/Superslicer sotto "Printer Settings" - "Custom G-code" e non modificando i G-code già esistenti, inserire `M117` nel campo "End G-code" e {% raw %}`M117 Layer {layer_num+1} of [total_layer_count]`{% endraw %} nel campo "Before layer change G-code", come da esempio seguente

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/prusaslicer-superslicer-layer.png" height="400">
</p>

dopo aver avviato la stampa apparirà il numero del layer in stampa al momento e il conteggio totale di layer, sia sull'interfaccia web che sul display della stampante (se presente e supportato).

### ULTIMAKER CURA

Per l'upload diretto su server con con Ultimaker Cura è necessario installare dal Marketplace il Plugin "OctoPrint Connection"

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/octoprint_connection.png" height="100">
</p>

una volta installato chiudere e riaprire Ultimaker Cura e andare su `Preferences --> Configure Cura...` selezionare `Printers` nel menu a sx, selezionare la propria stampante e infine cliccare su `Connect OctoPrint`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/connect_octoprint.png" height="50">
</p>

cliccare su `Add` ed inserire un nome, l'IP e la porta di Moonraker nei campi corrispondenti e cliccare su OK

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/add_moonraker.png" height="200">
</p>

una volta aggiunta l'istanza, inserire una API Key casuale (es: 1234567890) e cliccare su Connect

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/moonraker_octoprint_cura.png" height="300">
</p>

se tutti i passi sono stati effettuati correttamente ci si connetterà senza problemi a Moonraker e si potranno inviare i file direttamente dallo Slicer all'interfaccia Web. 

Ricordarsi di disabilitare: controllo accelerazione, coasting, extra restart distance e advance extruder pressure...

Per approfondimenti vai [QUI](https://github.com/KevinOConnor/klipper/blob/master/docs/Slicers.md){:target="_blank"}

- **Configurazione Opzionale per visualizzazione layer di stampa**

In caso si volesse visualizzare il numero di layer da interfaccia web (Fluidd o Mainsail) basta andare su Ultimaker Cura sotto il menu `Extensions --> Post Processing --> Modify G-Code` all'apertura del pop-up selezionare `Add a script` e `Display Filename And Layer On LCD`, come da esempio seguente

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/cura-layer-display.png" height="450">
</p>

dopo aver avviato la stampa apparirà il numero del layer in stampa al momento, il conteggio totale di layer e il nome del file in stampa, sia sull'interfaccia web che sul display della stampante (se presente e supportato).
