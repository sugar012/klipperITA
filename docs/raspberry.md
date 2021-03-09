---
layout: default
title: Raspberry
nav_order: 2
---

Installare RPI imager sul PC, inserire la MicroSD nel computer, quindi avviare Imager e selezionare “Choose OS”, poi su “Raspberry PI OS (other)”, quindi Raspberry PI Lite (32-bit).

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image6.png" height="180"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image1.png" height="180"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image20.png" height="180">
</p>

Premere su “Choose Sd card” e selezionare la microsd inserita precedentemente, quindi premere write ed acconsentire alla formattazione della MicroSD

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image8.png" height="180"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image5.png" height="180"> <img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image15.png" height="180">
</p>

Una volta che la scrittura e’ terminata, rimuovere la MicroSD dal pc e re-inserirla: comparirà un volume "boot"

Per poter abilitare SSH e WIFI direttamente al boot(headless mode) scaricare i [seguenti due files](https://github.com/Blaster1920/RPI_headless_tools/tree/main) cliccando su “Code”, poi “download zip”.
Decomprimere i due file direttamente nella root (cartella principale) della micro sd. 
Aprire con BLOCCO NOTE il file appena copiato denominato “wpa_supplicant.conf”. Dentro le virgolette mettere il SSID(nome della wifi) della tua wifi e sotto mettere la password della wifi.

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image12.png" height="280">
</p>

La microsd e’ ora pronta: toglierla dal computer ed inserirla nel Raspberry PI (da spento) ed alimentatelo. Aspettare qualche minuto per l’avvenuta connessione Wi-Fi

Avvalendosi del programma gratuito della Nirsoft “Wireless Network Watcher”, trovare l’ip locale del RPI, altrimenti ci si puo’ riferire alla pagina di gestione del proprio router.
Una volta che si ha l’IP, aprire il programma Bitvise SSH Client, e configurarlo come segue, tenendo cura di inserire l’ip del RPI trovato in precedenza. 

Inserire l’utente `pi` e la password di default `raspberry`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image11.png" height="380">
</p>

Una Volta inseriti i dati, premere login, apparirà una notifica che ci chiede se vogliamo salvare la chiave privata per il tunnel SSH, gli diciamo sì per sempre.

Avremo due schermate, una é il nostro terminale remoto in SSH, l’altra e’ il sFTP (cartelle e dati salvate sul rpi in accesso remoto). Per ora ci interessa il SSH, andiamo a digitare i primi comandi per aggiornare il sistema:

```shell
sudo apt-get update
```

```shell
sudo apt-get upgrade
```

Ora cambiamo la password di default con una a nostra scelta:

```shell
sudo passwd pi
```

Premiamo INVIO, poi digitiamo la nuova password (non c’e’ da preoccuparsi se non viene visualizzato niente nel terminale, e’ una misura di sicurezza).

Una volta finito di scriverla premiamo di nuovo INVIO. Potrebbe venire richiesta una conferma della password appena inserita, nel caso basta ri-digitarla e premere INVIO.. Una volta fatto riavviamo dando il comando:

```shell
sudo reboot
```

Bitvise ci notificherà della disconnessione avvenuta. Chiudiamo le finestre SSH e sFTP, clicchiamo su logout in basso, quindi cambiamo la password nella casella di testo con quella appena immessa. dopodiché aspettiamo che Bitwise si ricolleghi (in basso verrà notificato). Clicchiamo nuovamente login (dare 1 minuto al RPI per avviarsi) e andiamo sulla console SSH.

A questo punto siamo pronti ad installare Kiauh, il gestore che permette di installare comodamente Klipper, le API Moonraker e una webGUI a nostra scelta come Fluidd.
Bitvise ci notificherà della disconnessione avvenuta. Chiudiamo le finestre SSH e sFTP, clicchiamo su logout in basso, quindi cambiamo la password nella casella di testo con quella appena immessa. dopodiché aspettiamo che Bitwise si ricolleghi (in basso verrà notificato). Clicchiamo nuovamente login (dare 1 minuto al RPI per avviarsi) e andiamo sulla console SSH.

A questo punto siamo pronti ad installare Kiauh, il gestore che permette di installare comodamente Klipper, le API Moonraker e una webGUI a nostra scelta come Fluidd.
