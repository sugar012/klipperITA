<p align="center">
<a href="https://www.klipper3d.org"><img src="https://www.klipper3d.org/img/klipper-logo.png"</a>
</p>

# PREMESSA

>ATTENZIONE! Installare questo firmware richiede un minimo di manualità con linux e soprattutto con l’uso di Google, noi ci siamo impegnati a rendere la guida il più semplice possibile ma procedere a proprio rischio e leggere attentamente prima di acquistare il Raspberry.

>Klipper è un firmware che, sfruttando la potenza di calcolo di un Raspberry/PC Linux o derivati, riesce ad eseguire algoritmi complessi per il calcolo della cinematica offrendo inoltre la possibilità di raggiungere step rate più elevati.

>A differenza di Marlin, che gira sulla scheda della stampante ed è quindi limitato dalla potenza di calcolo di quest'ultima, Klipper esegue tutti i calcoli e invia le istruzioni alla scheda della stampante (anch'essa flashata con klipper per permettere la comunicazione) che deve solo eseguirli inviando i comandi ai motori/attuatori.

>Un'altra particolarità di questo firmware è la sua compatibilità con diverse interfacce web, potremo infatti scegliere tra 4 alternative: Fluidd, Mainsail, Octoprint e Duet.
Queste, oltre ad essere graficamente belle e curate, vanno a sostituire o affiancare lo schermo della stampante e sarà quindi più semplice gestire tutto con mouse e tastiera o tablet/smartphone!

>Tra gli altri vantaggi di klipper troviamo la possibilità di essere modificato senza alcuna compilazione: tramite l'interfaccia web è infatti possibile accedere al file di configurazione printer.cfg ed editarlo al volo. Basterà salvare e fare un restart del firmware et voilà! Vi dimenticherete di visual studio e di quelle mille righe di codice da scorrere ogni volta. Su klipper il printer.cfg funziona al contrario di Marlin: è vuoto e andremo ad aggiungere le funzioni dalla documentazione solo se ci interessano, questo rende più facile e veloce la configurazione.

>Per ulteriori approfondimenti qui un link con Le features di Klipper: klipper | Klipper is a 3d-printer firmware (klipper3d.org)

Adesso cominciamo!

---

## PREREQUISITI

Raspberry Pi, consigliato 3/4 (A+ o  B+) ma anche uno zero andrebbe bene (meno porte)
Micro SD Card (almeno 8Gb)

Programmi utili:
Bitwise SSH and sFTP client oppure WinSCP+Putty
Raspberry PI Imager

## PREPARAZIONE RASPBERRY PI

Installare RPI imager sul PC, inserire la MicroSD nel computer, quindi avviare Imager e selezionare “Choose OS”, poi su “Raspberry PI OS (other)”, quindi Raspberry PI Lite (32-bit).

<p align="center">
<img src="/images/image6.png" height="180"> <img src="/images/image1.png" height="180"> <img src="/images/image20.png" height="180">
</p>

Premere su “Choose Sd card” e selezionare la microsd inserita precedentemente, quindi premere write ed acconsentire alla formattazione della MicroSD

<p align="center">
<img src="/images/image8.png" height="180"> <img src="/images/image5.png" height="180"> <img src="/images/image15.png" height="180">
</p>

Una volta che la scrittura e’ terminata, rimuovere la MicroSD dal pc e re-inserirla: comparirà un volume "boot"

Per poter abilitare SSH e WIFI direttamente al boot(headless mode) scaricare i [seguenti due files](https://github.com/Blaster1920/RPI_headless_tools/tree/main) cliccando su “Code”, poi “download zip”.
Decomprimere i due file direttamente nella root (cartella principale) della micro sd. 
Aprire con BLOCCO NOTE il file appena copiato denominato “wpa_supplicant.conf”. Dentro le virgolette mettere il SSID(nome della wifi) della tua wifi e sotto mettere la password della wifi.

<p align="center">
<img src="/images/image12.png" height="280">
</p>

La microsd e’ ora pronta: toglierla dal computer ed inserirla nel Raspberry PI (da spento) ed alimentatelo. Aspettare qualche minuto per l’avvenuta connessione Wi-Fi

Avvalendosi del programma gratuito della Nirsoft “Wireless Network Watcher”, trovare l’ip locale del RPI, altrimenti ci si puo’ riferire alla pagina di gestione del proprio router.
Una volta che si ha l’IP, aprire il programma Bitvise SSH Client, e configurarlo come segue, tenendo cura di inserire l’ip del RPI trovato in precedenza. 

Inserire l’utente `pi` e la password di default `raspberry`

<p align="center">
<img src="/images/image11.png" height="380">
</p>

Una Volta inseriti i dati, premere login, apparirà una notifica che ci chiede se vogliamo salvare la chiave privata per il tunnel SSH, gli diciamo sì per sempre.

Avremo due schermate, una é il nostro terminale remoto in SSH, l’altra e’ il sFTP (cartelle e dati salvate sul rpi in accesso remoto). Per ora ci interessa il SSH, andiamo a digitare i primi comandi per aggiornare il sistema:

```sudo apt-get update```

```sudo apt-get upgrade```

Ora cambiamo la password di default con una a nostra scelta:

```sudo passwd pi```

Premiamo INVIO, poi digitiamo la nuova password (non c’e’ da preoccuparsi se non viene visualizzato niente nel terminale, e’ una misura di sicurezza).

Una volta finito di scriverla premiamo di nuovo INVIO. Potrebbe venire richiesta una conferma della password appena inserita, nel caso basta ri-digitarla e premere INVIO.. Una volta fatto riavviamo dando il comando:

```sudo reboot```

Bitvise ci notificherà della disconnessione avvenuta. Chiudiamo le finestre SSH e sFTP, clicchiamo su logout in basso, quindi cambiamo la password nella casella di testo con quella appena immessa. dopodiché aspettiamo che Bitwise si ricolleghi (in basso verrà notificato). Clicchiamo nuovamente login (dare 1 minuto al RPI per avviarsi) e andiamo sulla console SSH.

A questo punto siamo pronti ad installare Kiauh, il gestore che permette di installare comodamente Klipper, le API Moonraker e una webGUI a nostra scelta come Fluidd.


