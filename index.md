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
![image1](https://user-images.githubusercontent.com/53581505/110213185-2f190200-7e9f-11eb-8c7a-e7a37c011c5a.png =250x)
