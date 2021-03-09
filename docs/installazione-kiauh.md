---
layout: default
title: Installazione KIAUH
nav_order: 4
permalink: /installazione-kiauh/
---

{% include breadcrumbs.html %}

## INSTALLAZIONE KIAUH

Prepariamoci ad installare Kiauh con il comando:

```shell
sudo apt-get install git -y
```

Successivamente installare Kiauh digitando nella console le seguenti righe (comandi separati):

```shell
cd ~
git clone https://github.com/th33xitus/kiauh.git
./kiauh/kiauh.sh
```

A questo punto si aprira’ l’interfaccia di Kiauh:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image25.png" height="350">
</p>

A questo punto andremo ad installare le 3 parti fondamentali dell-ecosistema klipper: Klipper + Moonraker + Fluidd

- Entrare nel menu’ di installazione digitando `1` e premendo `INVIO`.

- Ora installare Klipper digitando ancora `1` e premendo `INVIO`.

- Allo stesso modo, sempre dal menù `1) [Install]`, installare moonraker digitando `2` e premere `INVIO`

Una volta installato moonraker, si ritornerà alla schermata principale premendo `Q` e dando `INVIO`.


Ora installiamo la nostra WebUI preferita. Per i novizi che non hanno mai usato Klipper in precedenza, e per chiunque prediliga la stabilita’ e velocita’ dei servizi, consigliamo Fluidd.

Per installare la WebUI, digitare il numero corrispondente (nel caso di fluidd il 4) e premere `INVIO`.
Se viene richiesta l’installazione di macro, rispondere `y`.

Se tutto è andato correttamente dovreste trovarvi davanti una situazione del genere:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image26.png" height="350">
</p>

Complimenti, ora avete correttamente installato Klipper e la WebUI sul vostro Raspberry, siete a metà strada dalla vostra prima stampa con Klipper! :P
