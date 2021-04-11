---
layout: default
title: Installazione e Configurazione Firmware
parent: Installazione su Raspberry
nav_order: 4
has_children: false
permalink: /installazione-rpi/configurazione-firmware/
---

# Installazione e Configurazione Firmware
{: .fw-400 }

Prima di iniziare la configurazione è necessario recuperare la stringa della seriale della nostra stampante.
Ancora su tornare al menù advanced:

Qui, a stampante accesa e collegata al Raspberry, selezionate la voce `6) [Get MCU ID]`

Se il flashing del firmware è andato correttamente e la stampante comunica con il nostro Raspberry, KIAUH ci restituirà una stringa del tipo: 

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image2.png" height="350">
</p>

Copiamo questa stringa (ci servirà dopo).

La parte difficile è adesso finita! Da ora in poi useremo l’interfaccia web :)

Se tutto è andato correttamente e il Raspberry è collegato alla nostra rete LAN, inserendo il suo indirizzo IP su un browser di qualunque dispositivo collegato alla rete di casa dovrebbe comparire l’interfaccia web scelta (negli esempi seguenti l'interfaccia Fluidd).

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image3.png" height="350">
</p>

Tramite l’interfaccia web è possibile editare il file printer.cfg. Cliccare in alto a destra sulla voce **PRINTER**

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image28.png" height="50">
</p>

si aprirà un menù come questo:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image29.png" height="350">
</p>

Cliccare sul file printer.cfg, comparirà un menù a tendina, cliccare su edit.

Si aprirà adesso un editor di testo, copiare e sostituire quindi il contenuto del file config scaricato precedentemente all’interno dell’editor dell'interfaccia,  all'interno del file alla voce [mcu] incollare la stringa precedentemente trovata in questo modo:

```
[mcu]
serial:  /dev/serial/by-id/…
```

Chiudere quindi il nostro printer.cfg premendo il pulsante in rosso `SAVE AND RESTART`

Se dovessero esserci errori solitamente l’interfaccia ci suggerisce cosa non va bene o ci suggerisce le voci mancanti, cercare quindi la voce suggerita all’interno del printer.cfg e controllare i parametri/pin o se non c’è la voce aggiungerla.

Per aggiungere una funzionalità al nostro nuovo firmware, anziché decommentare (come si faceva su Marlin) in questo caso andremo ad aggiungere pezzi di config copiandoli e incollandoli.

In questa pagina sono presenti tutte le funzioni che questo firmware può offrire ed è possibile aggiungerle semplicemente facendo copia&incolla nel nostro printer.cfg e configurandole cambiando con i valori adatti alla nostra stampante.

Ricordiamo che dove è presente il cancelletto (#) la riga viene disabilitata e trattata come un commento.

Ora tocca a voi navigare tra la [Documentazione](https://github.com/KevinOConnor/klipper/tree/master/docs){:target="_blank"} di Klipper per completare e affinare la vostra configurazione!
