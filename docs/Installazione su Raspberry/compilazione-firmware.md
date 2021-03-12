---
layout: default
title: Compilazione Firmware
parent: Guida installazione su Raspberri Pi
nav_order: 4
has_children: false
permalink: /compilazione-firmware/
---

{% include breadcrumbs.html %}

## COMPILAZIONE FIRMWARE E FLASH SU STAMPANTE

Per comunicare correttamente con la stampante la scheda di quest’ultima deve essere flashata per Klipper. 
Per compilare e flashare la scheda stampante verrà usato ancora una volta Kiauh.

🟥**IMPORTANTE**: Recuperare da [quì](https://github.com/KevinOConnor/klipper/tree/master/config) il file.cfg relativo alla propria stampante o scheda utilizzata, perchè sarà il file dove andremo a configurare i parametri aggiuntivi oltre a quelli presenti di default.

🟥**IMPORTANTE**: Nella parte iniziale del file ci sono svariate righe di testo con dei # davanti, leggerle attentamente e tenerle a portata di mano perchè ci indicano le impostazioni per creare il firmware al passo successivo.

Su Kiauh selezionare la voce `4) Advanced` e si aprirà il seguente menù:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image24.png" height="350">
</p>

Se la vostra scheda prevede il flash da USB (leggete nelle prime righe del config) selezionare la voce 4) altrimenti la 5).

Si aprirà la schermata seguente:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image16.png" height="350">
</p>

**MODIFICARE** adesso le impostazioni di compilazione **come suggerito nel file di esempio scaricato precedentemente** (i suggerimenti sono nella parte alta del file .cfg)

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image27.png" height="350">
</p>

seguire nel dettaglio ogni impostazione e fare attenzione se sono previsti comandi aggiuntivi da eseguire dopo il make del firmware.

Solo quando siamo sicuri di aver terminato, colleghiamo la stampante (accesa) via USB al Raspberry premiamo il tasto `q` e successivamente `y` per confermare. 

Ora inizierà la compilazione e successivo flash della scheda stampante.

Se invece la vostra scheda prevede il flash da SDcard dovrete estrarre i file firmware.bin ed effettuare il flash manualmente mettendolo sulla SDcard e inserendola nella stampante.

Fare attenzione che alcune schede come ad esempio la MKS Robin Nano, hanno bisogno di comandi aggiuntivi dopo il make del firmware, questi sono indicati sempre nella parte alta del printer.cfg.
