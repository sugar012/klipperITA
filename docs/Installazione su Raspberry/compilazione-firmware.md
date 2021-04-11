---
layout: default
title: Compilazione Firmware
parent: Installazione su Raspberry
nav_order: 3
has_children: false
permalink: /installazione-rpi/compilazione-firmware/
---

# Compilazione Firmware e Flash su Stampante 3D
{: .fw-400 }

Per comunicare correttamente con la stampante la scheda di quest’ultima deve essere flashata per Klipper. 
Per compilare e flashare la scheda stampante verrà usato ancora una volta Kiauh.

🟥**ATTENZIONE**: Se la Stampante 3D è dotata di un Display Touchscreen, installando Klipper si perderanno tutte le funzionalità del Display, ovvero il Display Touchscreen non funzionerà più!!! Nessun problema perchè tutte le funzionalità, se non maggiori funzionalità saranno presenti sulla WebUI. Con Klipper il Display della Stampante 3D è solo superfluo.

🟥**IMPORTANTE**: Recuperare da [QUI](https://github.com/KevinOConnor/klipper/tree/master/config) il file.cfg relativo alla propria stampante (es: `printer-creality-ender3-2018.cfg`) o scheda (board) utilizzata (es: `generic-bigtreetech-skr-v1.3.cfg`), perchè sarà il file dove andremo a configurare i parametri aggiuntivi oltre a quelli presenti di default.

🟥**IMPORTANTE**: Nella parte iniziale del file ci sono svariate righe di testo con dei `#` davanti, leggerle attentamente e tenerle a portata di mano perchè indicano le impostazioni per creare il firmware al passo successivo.

Su KIAUH selezionare la voce `4) Advanced` e si aprirà il seguente menù:

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

Se invece la vostra scheda prevede il flash solamente da MicroSD card dovrete scaricare sul PC il file `klipper.bin` che è presente al percorso `~/klipper/out` del Raspberry Pi, rinominarlo in `firmware.bin`, copiare il file sulla MicroSD card, una volta copiato, inserire la MicroSD card nella stampante spenta, accendere la stampante ed attendere **circa 1 minuto**, se tutto sarà andato per la meglio, reinserendo la MicroSD sul PC troverete un file denominato `FIRMWARE.CUR`, cià significa che il firmware è stato correttamente installato sulla scheda della stampante.

Fare attenzione che alcune schede come ad esempio la MKS Robin Nano, hanno bisogno di comandi aggiuntivi dopo il make del firmware, questi sono indicati sempre nella parte alta del printer.cfg.
