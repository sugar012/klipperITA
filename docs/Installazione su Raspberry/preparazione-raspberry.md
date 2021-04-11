---
layout: default
title: Preparazione Raspberry Pi
nav_order: 1
parent: Installazione su Raspberry
permalink: /installazione-rpi/preparazione-raspberry/
---

# Preparazione Raspberry Pi
{: .fw-400 }

Installare Raspberry Pi imager sul PC, inserire la MicroSD nel computer, quindi avviare Imager e selezionare “Choose OS”, poi su “Raspberry Pi OS (other)”, quindi Raspberry Pi OS Lite (32-bit).

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image6.png" width="350"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image1.png" width="350"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image20.png" width="350">
</p>

Premere su “Choose Sd card” e selezionare la microsd inserita precedentemente, quindi premere write ed acconsentire alla formattazione della MicroSD

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image8.png" width="350"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image5.png" width="350"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image15.png" width="350">
</p>

Una volta che la scrittura e’ terminata, rimuovere la MicroSD dal PC e re-inserirla: comparirà un volume "boot"

Per poter abilitare SSH e WIFI direttamente al boot(headless mode) scaricare i [seguenti due files](https://github.com/Blaster1920/RPI_headless_tools/tree/main){:target="_blank"} cliccando su “Code”, poi “download zip”.
Decomprimere i due file direttamente nella root (cartella principale) della micro sd. 
Aprire con BLOCCO NOTE il file appena copiato denominato `wpa_supplicant.conf`. Dentro le virgolette mettere il `SSID`, cioè il nome della propria rete Wi-Fi e sotto, alla voce `psk` inserire sempre fra virgolette la password della propria rete Wi-Fi.

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image12.png" width="600">
</p>

La MicroSD è ora pronta: toglierla dal computer, inserirla nel Raspberry Pi (da spento) ed alimentarlo. Aspettare qualche minuto per l’avvenuta connessione Wi-Fi

Avvalendosi del programma gratuito della Nirsoft “Wireless Network Watcher”, trovare l’indirizzo IP locale del RPi, altrimenti ci si puo’ riferire alla pagina di gestione del proprio router.
Una volta che si ha l’indirizzo IP, aprire il programma Bitvise SSH Client, e configurarlo come segue, tenendo cura di inserire l’indirizzo IP del RPi trovato in precedenza. 

Inserire l’utente `pi` e la password di default `raspberry`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image11.png" width="380">
</p>

Una volta inseriti i dati, premere login, apparirà una notifica che ci chiede se vogliamo salvare la chiave privata per il tunnel SSH, gli diciamo sì per sempre.

Avremo due schermate, una é il nostro terminale remoto in SSH, l’altra e’ il sFTP (cartelle e dati salvate sul rpi in accesso remoto). Per ora ci interessa il SSH, andiamo a digitare i primi comandi per aggiornare il sistema:

```shell
sudo apt-get update
```

```shell
sudo apt-get upgrade
```

Ora cambiamo la password di default con una a nostra scelta:

```shell
passwd pi
```

Premiamo INVIO, poi digitiamo la nuova password (non c’è da preoccuparsi se non viene visualizzato niente nel terminale, è una misura di sicurezza).

Una volta finito di scriverla premiamo di nuovo INVIO. Potrebbe venire richiesta una conferma della password appena inserita, nel caso basta ri-digitarla e premere INVIO. Una volta fatto riavviamo digitando il comando:

```shell
sudo reboot
```

Bitvise ci notificherà della disconnessione avvenuta. Chiudiamo le finestre SSH e sFTP, clicchiamo su logout in basso, quindi cambiamo la password nella casella di testo con quella appena immessa. Dopodiché aspettiamo che Bitvise si ricolleghi (in basso verrà notificato). Clicchiamo nuovamente login (dare 1 minuto al RPi per avviarsi) e andiamo sulla console SSH.

A questo punto siamo pronti ad installare KIAUH, il gestore che permette di installare comodamente Klipper, le API Moonraker e una webGUI a nostra scelta come ad esempio Fluidd.
