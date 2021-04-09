---
layout: default
title: Installazione KIAUH
parent: Installazione su Raspberry
nav_order: 3
permalink: /installazione-rpi/installazione-kiauh/
---

# Installazione KIAUH

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

## Aggiornamento KIAUH

Ad ogni aggiornamento di KIAUH potrebbero essere introdotti bug fixing oppure nuove funzionalità, per questo motivo sarebbe opportuno verificare ogni tanto se sono presenti aggiornamenti e procedere all'installazione.

Inoltre è possibile verificare eventuali aggiornamenti importanti consultando il [CHANGELOG di KIAUH](https://github.com/th33xitus/kiauh/blob/master/docs/changelog.md){:target="_blank"}.

Per verificare se sono presenti aggiornamenti ed installarli automaticamente è possibile procedere lanciando i seguenti comandi

```shell
cd ~
cd kiauh
git pull
cd ~
```

se sono presenti aggiornamenti verranno scaricati i nuovi file, in caso contrario si presenterà il messaggio `Already up to date`, che vuol dire che si è già all'ultima versione disponibile.

In caso siano stati scaricati aggiornamenti, lanciando nuovamente KIAUH con il comando `./kiauh/kiauh.sh` potremo verificare la nuova versione, che nel seguente esempio è la `v3.0-37`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/kiauh_upgraded.png" height="350">
</p>

Successivamente sarà possibile entrare nei vari menu per verificare eventuali cambiamenti o funzionalità aggiunte nella nuova versione.
