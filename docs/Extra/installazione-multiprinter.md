---
layout: default
title: Installazione Multiprinter
parent: Extra
nav_order: 3
has_children: false
permalink: /extra/installazione-multiprinter/
---

# Installazione Multiprinter
{: .fw-400 }

KIAUH permette inoltre l’installazione automatica di due o più istanze di Klipper per poter gestire più stampanti.Il procedimento è simile all’installazione semplice con la sola differenza che quando KIAUH ci chiederà quante istanze installare andremo ad inserire il numero che ci interessa:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image7.png" width="350">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image23.png" width="350">
</p>

Una volta installate le due istanze di klipper riavviamo con 
```shell
sudo reboot
```
Riavviamo KIAUH e scegliamo l’installazione di MOONRAKER.
A questo punto KIAUH è consapevole dell’installazione di più installazioni di klipper e ci chiederà di installare altrettante istanze di MOONRAKER

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image14.png" height="450">
</p>

Di default vengono create le istanze MOONRAKER con le porte successive a 7125. Ovvero con due istanze la seconda avrà come porta 7126.
Verranno quindi create 2 cartelle distinte con all’interno printer.cfg e moonraker.conf da poter impostare a piacimento.

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image19.png" height="350">
</p>

Il resto dell’installazione è coma una normale procedura descritta sopra: installazione del frontend (FLUIDD o MAINSAIL o altro) e quanto ne consegue.

Per poter gestire le stampanti da FLUIDD, ad esempio, basterà recarsi all’indirizzo della stampante nel browser (cosiddetta printer1) e dal menu a destra selezionare `add another printer`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image10.png" height="100">
</p>

Basterà mettere `IP:PORTA` della seconda istanza di moonraker per ritrovarsi a gestirle entrambe facendo un semplice switch dallo stesso menu

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image18.png" height="300">
</p>

Una cosa aggiuntiva che è possibile fare è l’upload diretto(e stampa) da slicer.
Prima di tutto andremo a creare due cartelle separate dove fare l’upload dei gcode dove MOONRAKER+FLUIDD andranno a pescare.E’ possibile scegliere quale cartella si vuole, ad esempio nella directory principali sdcard1 e sdcard2:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image9.png" height="100">
</p>

Successivamente andremo ad inserire nei rispettivi printer.cfg delle stampanti le directory dove punteranno per il salvataggio/lettura dei gcode.

```
[virtual_sdcard]
path: ~/sdcard1
```

e

```
[virtual_sdcard]
path: ~/sdcard2
```

A questo punto aprire i rispettivi moonraker.conf e aggiungere questa stringa:

```
[octoprint_compat]
```

Passiamo ora allo slicer
Con Prusaslicer/Superslicer basta mettere indirizzo `IP:PORTA` della rispettiva istanza MOONRAKER dentro alla configurazione per octoprint della stampante fisica e i file verranno inviate rispettivamente alle cartelle impostate.
