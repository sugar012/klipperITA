<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/title.png" >
</p> 

## PREMESSA

>ATTENZIONE! Installare questo firmware richiede un minimo di manualità con linux e soprattutto con l’uso di Google, noi ci siamo impegnati a rendere la guida il più semplice possibile ma procedere a proprio rischio e leggere attentamente prima di acquistare il Raspberry.

>Klipper è un firmware che, sfruttando la potenza di calcolo di un Raspberry/PC Linux o derivati, riesce ad eseguire algoritmi complessi per il calcolo della cinematica offrendo inoltre la possibilità di raggiungere step rate più elevati.

>A differenza di Marlin, che gira sulla scheda della stampante ed è quindi limitato dalla potenza di calcolo di quest'ultima, Klipper esegue tutti i calcoli e invia le istruzioni alla scheda della stampante (anch'essa flashata con klipper per permettere la comunicazione) che deve solo eseguirli inviando i comandi ai motori/attuatori.

>Un'altra particolarità di questo firmware è la sua compatibilità con diverse interfacce web, potremo infatti scegliere tra 4 alternative: Fluidd, Mainsail, Octoprint e Duet.
Queste, oltre ad essere graficamente belle e curate, vanno a sostituire o affiancare lo schermo della stampante e sarà quindi più semplice gestire tutto con mouse e tastiera o tablet/smartphone!

>Tra gli altri vantaggi di klipper troviamo la possibilità di essere modificato senza alcuna compilazione: tramite l'interfaccia web è infatti possibile accedere al file di configurazione printer.cfg ed editarlo al volo. Basterà salvare e fare un restart del firmware et voilà! Vi dimenticherete di visual studio e di quelle mille righe di codice da scorrere ogni volta. Su klipper il printer.cfg funziona al contrario di Marlin: è vuoto e andremo ad aggiungere le funzioni dalla documentazione solo se ci interessano, questo rende più facile e veloce la configurazione.

>Per ulteriori approfondimenti qui un link con le [features di Klipper](https://www.klipper3d.org/Features.html)

Adesso cominciamo!

---

## MENU

* [PREREQUISITI](https://github.com/sugar012/klipperITA/blob/main/index.md#prerequisiti)

* [PREPARAZIONE RASPBERRY PI](https://github.com/sugar012/klipperITA/blob/main/index.md#preparazione-raspberry-pi)

* [TVBOX](https://github.com/sugar012/klipperITA/blob/main/index.md#per-chi-ha-seguito-la-guida-per-tvbox-proseguire-da-questo-punto-in-avanti)

* [INSTALLAZIONE KIAUH](https://github.com/sugar012/klipperITA/blob/main/index.md#installazione-kiauh)

* [COMPILAZIONE FIRMWARE E FLASH SU STAMPANTE](https://github.com/sugar012/klipperITA/blob/main/index.md#compilazione-firmware-e-flash-su-stampante)

* [CONFIGURAZIONE](https://github.com/sugar012/klipperITA/blob/main/index.md#configurazione)

* [SETTAGGI SLICER](https://github.com/sugar012/klipperITA/blob/main/index.md#settaggi-slicer)

* [CALIBRAZIONI](https://github.com/sugar012/klipperITA/blob/main/index.md#calibrazioni)

* [ALTRI LINK UTILI](https://github.com/sugar012/klipperITA/blob/main/index.md#altri-link-utili)

* [F.A.Q. aka Domande Frequenti](https://github.com/sugar012/klipperITA/blob/main/index.md#faq-aka-domande-frequenti)

* [INSTALLAZIONE MULTIPRINTER](https://github.com/sugar012/klipperITA/blob/main/index.md#installazione-multiprinter)

* [INSTALLAZIONE MULTIPRINTER](https://github.com/sugar012/klipperITA/blob/main/index.md#installazione-multicam)

* [COMMUNITY](https://github.com/sugar012/klipperITA/blob/main/index.md#community)




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

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


### 📢Per chi ha seguito la guida per TVBOX proseguire da questo punto in avanti📢

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

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


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

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


## CONFIGURAZIONE


Prima di iniziare la configurazione è necessario recuperare la stringa della seriale della nostra stampante.
Ancora su Kiauh tornare al menù advanced:

Qui, a stampante accesa e collegata al Raspberry, selezionate la voce `6) [Get MCU ID]`

Se il flashing del firmware è andato correttamente e la stampante comunica con il nostro Raspberry, Kiauh ci restituirà una stringa del tipo: 

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image2.png" height="350">
</p>

Copiamo questa stringa (ci servirà dopo).

La parte difficile è adesso finita! Da ora in poi useremo l’interfaccia web :)

Se tutto è andato correttamente e il Raspberry è collegato alla nostra rete LAN, inserendo il suo indirizzo IP su un browser di qualunque dispositivo collegato alla rete di casa dovrebbe comparire l’interfaccia web scelta.

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

Ora tocca a voi navigare tra i [DOC](https://github.com/KevinOConnor/klipper/tree/master/docs) di Klipper per completare e affinare la vostra configurazione!

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


## SETTAGGI SLICER

Per l'upload diretto su server con Prusaslice/Superslicer basta inserie l' IP del server come di seguito:
<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image13.png" height="350">
</p>

Mentre con Ultimaker Cura è necessario installare dal Marketplace il Plugin "OctoPrint Connection"

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/octoprint_connection.png" height="100">
</p>

una volta installato chiudere e riaprire Ultimaker Cura e andare su "Preferences --> Configure Cura..." selezionare "Printers" nel menu a sx, selezionare la propria stampante e infine cliccare su "Connect OctoPrint"

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/connect_octoprint.png" height="50">
</p>

cliccare su "Add" ed inserire un nome, il proprio IP di Moonraker e la porta e cliccare su OK

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/add_moonraker.png" height="200">
</p>

una volta aggiunta l'istanza, inserire una API Key casuale (es: 1234567890) e cliccare su Connect

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/moonraker_octoprint_cura.png" height="300">
</p>

se tutti i passi sono stati effettuati correttamente ci si connetterà senza problemi a Moonraker e si potranno inviare i file direttamente dallo Slicer all'interfaccia Web. 


Ricordarsi di disabilitare: controllo accelerazione, coasting, extra restart distance e advance extruder pressure..

Per approfondimenti vai [QUI](https://github.com/KevinOConnor/klipper/blob/master/docs/Slicers.md)

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


## CALIBRAZIONI

* [Bed Leveling](https://www.klipper3d.org/Bed_Level.html) - Come calibrare il piatto usando Klipper
* [E-Steps](https://github.com/KevinOConnor/klipper/blob/master/docs/Rotation_Distance.md#calibrating-rotation_distance-on-extruders) - Calibrazione degli steps estrusore
* [Pressure Advance](https://github.com/KevinOConnor/klipper/blob/master/docs/Pressure_Advance.md) - Per gestire la pressione del filamento e avere angoli più netti
* [Resonance Compensation](https://www.klipper3d.org/Resonance_Compensation.html) - Per eliminare il ghosting dovuto alla risonanza della stampante

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


## ALTRI LINK UTILI


* [https://www.klipper3d.org/Rotation_Distance.html](https://www.klipper3d.org/Rotation_Distance.html) / [Post su Telegram](https://t.me/Klipper3DITA/24399) - Gli “step/mm” di Klipper
* [Config changes](https://github.com/KevinOConnor/klipper/blob/master/docs/Config_Changes.md) - Da visionare prima di ogni upgrade
* [Config Reference](https://github.com/KevinOConnor/klipper/blob/master/docs/Config_Reference.md) - In dettaglio ogni sezione del file di configurazione
* [G-Codes](https://github.com/KevinOConnor/klipper/blob/master/docs/G-Codes.md) - Lista dei gcodes e comandi ammessi in klipper
* [Bed Mesh e Homing con probe ed endstop separati](https://github.com/KevinOConnor/klipper/blob/master/docs/Bed_Mesh.md#the-relative-reference-index) 
* [Plugins Moonraker](https://github.com/Arksine/moonraker/blob/master/docs/configuration.md) - (per esempio per spegnere e accendere la stampante con relè)
* [Come aggiungere una webcam all’interfaccia web](https://docs.google.com/document/d/1AqtBhPTZOei1bds82Q2bN_Hy5QSHhvsh3vqAmPzSiJo) - Pagina 4


[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***


## F.A.Q. aka Domande Frequenti

Se non trovi una domanda con relativa risposta scrivine una di seguito, risponderemo quando possibile.

-Dove trovo il config per la mia stampante? 
Dentro la cartella `config` della vostra o installazione o [Qui](https://github.com/KevinOConnor/klipper/tree/master/config)

-Come faccio a calibrare il piatto? 
[Qui](https://github.com/sugar012/klipperITA/blob/main/index.md#calibrazioni)

-Dove devo mettere il file config della mia stampante?
nella cartella `klipper_config`

[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)
***

## INSTALLAZIONE MULTIPRINTER

KIAUH permette inoltre l’installazione automatica di due o più istanze di Klipper per poter gestire più stampanti.Il procedimento è simile all’installazione semplice con la sola differenza che quando KIAUH ci chiederà quante istanze installare andremo ad inserire il numero che ci interessa:

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image7.png" height="450">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image23.png" height="450">
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
Con Prusaslicer/Superslicer basta mettere indirizzo `IP:PORTA` della rispettiva istanza MOONRAKER dentro alla configurazione per octoprint della stampante fisica e i file verranno inviate rispettivamente alle cartelle impostate. Consultare la sezione [SETTAGGI SLICER](https://github.com/sugar012/klipperITA/blob/main/index.md#settaggi-slicer)


---


## INSTALLAZIONE MULTICAM


Per poter utilizzare due o più webcam con MJPG-Streamer (avendo seguito la [guida](https://github.com/sugar012/klipperITA/blob/main/index.md#altri-link-utili) basta aggiungere un altra coppia di scripts per l'avvio automatico nella cartella scripts.

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image30.png" height="100">
</p>

e dare i seguenti comandi:

```shell
sudo chmod +x /home/TUOUSER/scripts/webcam1
sudo chmod +x /home/TUOUSER/scripts/webcamDaemon1
```

Con il seguente comando troveremo a quali /dev/video il nostro sistema ha assegnato le cam:

```shell
v4l2-ctl --list-devices
```

che ci restituirà una cosa simile a:

```shell
pi@raspberrypi:~ $ v4l2-ctl --list-devices
bcm2835-codec-decode (platform:bcm2835-codec):
        /dev/video10
        /dev/video11
        /dev/video12

bcm2835-isp (platform:bcm2835-isp):
        /dev/video13
        /dev/video14
        /dev/video15
        /dev/video16

USB2.0 PC CAMERA: USB2.0 PC CAM (usb-0000:01:00.0-1.3):
        /dev/video0
        /dev/video1

USB 2.0 PC Cam (usb-0000:01:00.0-1.4):
        /dev/video2
        /dev/video3
```

Le nostre webcam saranno quindi distinte in `/dev/video0` e `/dev/video2`

Ora modifichiamo i due file `webcamDaemon` aggiungendo a quale device dovranno connettersi e farli uscire con due porte distinte

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image31.png" height="650">
</p>

Nel file `webcamDaemon1` basterà sosituire `/dev/video0` con `/dev/video2` e cambiare la porta con 8081

Sostituiamo anche la stringa in `webcam1` come di seguito

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image32.png" height="450">
</p>

In ultimo andiamo quindi ad inserire nel file `/etc/rc.local` la stringa per l'avvio della seconda istanza 

```
home/TUOUSER/scripts/webcam1 start
```


[torna al menu](https://github.com/sugar012/klipperITA/blob/main/index.md#menu)

***

## COMMUNITY

* [Discord (internazionale)](https://discord.klipper3d.org/)
* [Gruppo Telegram Italiano](https://t.me/Klipper3DITA)
* [Gruppo Facebook Italiano](https://www.facebook.com/groups/2753077415021752)



Grazie a: laurienzu, Factotum_res, Jacopo Franco, sugar0

Per aver creato questa guida!




