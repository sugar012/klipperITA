---
layout: default
title: Installazione Moonraker-Telegram
parent: Extra
nav_order: 2
has_children: false
permalink: /extra/installazione-moonraker-telegram/
---

# Installazione moonraker-telegram
{: .fw-400 }
{: .no_toc }

Con questo plugin è possibile inviare a un bot Telegram messaggi sullo stato delle stampe 3D comprensivi di foto (ovviamente solo se è stata configurata una Cam sul Raspberry Pi).

---

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

Se non si possiede già un bot Telegram è necessario procedere alla creazione seguendo tutti i passi della guida, mentre se si è già in possesso di un bot Telegram basta seguire la guida dal punto [Installare lo script su un Raspberry Pi](#installare-lo-script-su-un-raspberry-pi).

## Creazione di un bot Telegram

Cerca lo user @BotFather all'interno dell'applicazione Telegram

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/botfather-logo.png" height="75">
</p>

Clicca su Start per iniziare una conversazione con @BotFather

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/botfather-home.png" height="500">
</p>

Invia il comando `/newbot` a @BotFather. @BotFather risponderà:

{% raw %}
```
Alright, a new bot. How are we going to call it? Please choose a name for your bot.
```
{% endraw %}

Inserisci il nome del bot che vuoi creare (es: Pippo) e @BotFather risponderà:

{% raw %}
```
Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.

ATTENZIONE: questo non sarà lo @username del nuovo bot Telegram. Lo @username verrà creato al prossimo passo.
```
{% endraw %}

Invia lo `username` desiderato per il tuo bot a @BotFather seguito da `_bot` (es: Pippo_bot) e @BotFather risponderà con una serie di frasi fra cui la HTTP API token:

{% raw %}
```
Done! Congratulations on your new bot. You will find it at t.me/Pippo_bot. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.

Use this token to access the HTTP API:
<HTTP API token>
Keep your token secure and store it safely, it can be used by anyone to control your bot.

For a description of the Bot API, see this page: https://core.telegram.org/bots/api
```
{% endraw %}

Inizia una conversazione col tuo nuovo bot. Clicca sul link `t.me/<bot-username>` nella risposta di @BotFather’s e clicca su Start in basso sulla chat che si aprirà. Il bot appena creato apparirà nella lista delle chat Telegram.

## Recuperare l'access token della API Telegram

Il bot @BotFather invierà una API access token non appena creato il tuo bot. Per recuperare il tuo token relativo al bot, vedi la precedente sezione. Se non riesci a trovare la API access token, crea un nuovo token seguendo i passi indicati di seguito.

Invia `/token` a @BotFather

Seleziona il bot che interessa dalla lista. @BotFather risponderà con una API access token:

{% raw %}
```
You can use this token to access HTTP API:
<API-access-token>

For a description of the Bot API, see this page: https://core.telegram.org/bots/api
```
{% endraw %}

## Recuperare la chat ID di Telegram

Incolla il seguente link nel browser. Sostituisci <API-access-token> con la API access token che hai creato nella precedente sezione:

{% raw %}
```
https://api.telegram.org/bot<API-access-token>/getUpdates?offset=0
```
{% endraw %}

Invia un messaggio al tuo bot tramite l'applicazione Telegram. Il contenuto del messaggio può essere qualunque frase. La cronologia della chat dovrà contenere almeno un messaggio per poter recuperare la chat ID.
Effettua un refresh del browser (lo si può fare anche premendo il tasto F5 sulla tastiera del PC).

Recuperare il valore numerico di chat ID ricercando l'id all'interno dell'oggetto JSON. Nell'esempio seguente la `chat ID` è `123456789`.

{% raw %}
```
{  
   "ok":true,
   "result":[  
      {  
         "update_id":XXXXXXXXX,
         "message":{  
            "message_id":2,
            "from":{  
               "id":123456789,
               "first_name":"XYZ",
               "last_name":"ZYX"
            },
            "chat":{  
               "id":123456789,
               "first_name":"XYZ",
               "last_name":"ZYX",
               "type":"private"
            },
            "date":1487183963,
            "text":"Ciao"
         }
      }
   ]
}
```
{% endraw %}

In alternativa, tramite l'App Telegram è possibile scrivere al bot [GetIDs Bot](https://t.me/getidsbot), il bot risponderà con la `chat ID`, che non è altro che il valore numerico del campo `id` (nell'esempio seguente `12345678`):

{% raw %}
```
👤 You
 ├ id: 12345678
 ├ is_bot: false
 ├ first_name: XYZ
 ├ username: XYZ (https://t.me/XYZ)
 ├ language_code: en (-)
 └ created: ~ 2/2014 (?) (https://t.me/getidsbot?start=idhelp)
 ```
  {% endraw %}

## Installare lo script su un Raspberry Pi

Innanzitutto verifica di aver aggiunto la stringa `[display_status]` alla configurazione di klipper. Se già presente non è necessario effettuare operazioni.

Se è la prima volta che procedi allo scaricamento del plugin è necessario utilizzare i seguenti comandi SSH

```shell
cd
git clone https://github.com/Raabi91/moonraker-telegram
```

## Installazione singola istanza

**ATTENZIONE: Questa configurazione è necessaria se si possiede un Raspberry Pi connesso a una sola stampante 3D.
Se si possiedono più stampanti 3D connesse a un solo Raspberry Pi seguire i punti alla sezione [Installazione istanze multiple](#installazione-istanze-multiple)**

Una volta scaricato lo script come indicato sopra è possibile procedere all'installazione con i seguenti comandi

```shell
cd moonraker-telegram
chmod 755 ./scripts/install.sh
./scripts/install.sh
```

durante l'installazione ti verrà richiesto di indicare il percorso contenente il file di configurazione di moonraker:

{% raw %}
```
your moonraker config path (like /home/pi/klipper_config):
```
{% endraw %}

inserire il percorso di default che sarà il seguente

{% raw %}
```
/home/pi/klipper_config
```
{% endraw %}

successivamente verrà richiesto se si desidera configurare installazioni multiple:

{% raw %}
```
if you want to use multiple instances on one pi, enter an identifier here. this is needed to create the sytemd service
If you only use it once per hardware, simply press enter.
```
{% endraw %}

essendo una installazione su istanza singola è necessario solo confermare premendo invio.

Da questo punto in poi sarà possibile modificare la configurazione utilizzando l'interfaccia web di Mainsail o Fluidd, modificando il file `telegram_config.sh`

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/telegram-config.png" height="350">
</p>

nelle sezioni `token` e `chatid` inserendo i rispettivi valori creati nei passi precedenti:

{% raw %}
```
# Your telegram bot token
token="<bot-token>"
# Your chat ID
chatid="<chat-id>"
```
{% endraw %}

al termine delle modifiche è necessario riavviare moonraker-telegram da SSH con il seguente comando

```shell
sudo systemctl restart moonraker-telegram
```

Se è stato eseguito tutto a dovere, all'avvio di una stampa verrà inviata una notifica su Telegram all'interno del proprio bot.

## Installazione istanze multiple

**ATTENZIONE: Questa configurazione è opzionale ed è necessaria solo se si possiedono due stampanti 3D connesse allo stesso Raspberry Pi e si vogliono ricevere notifiche su due bot separati. Ciò implica a sua volta che siano presenti due istanze distinte e separate di moonraker.**

Se provieni da una singola istanza procediamo quanto segue:

```shell
cd
git clone https://github.com/Raabi91/moonraker-telegram moonraker-telegram2
cd moonraker-telegram2
chmod 755 ./scripts/install.sh
./scripts/install.sh
```

durante l'installazione ti verrà richiesto di indicare il percorso contenente il file di configurazione di moonraker:

{% raw %}
```
your moonraker config path (like /home/pi/klipper_config):
```
{% endraw %}

Inserire il percorso di del secondo config di klipper che avete scelto nell'installazione multiprinter. Se avete seguito la guida sarà:

{% raw %}
```
/home/pi/klipper_config/printer_2
```
{% endraw %}

Successivamente verrà richiesto se si desidera configurare installazioni multiple:

{% raw %}
```
if you want to use multiple instances on one pi, enter an identifier here. this is needed to create the sytemd service
If you only use it once per hardware, simply press enter.
```
{% endraw %}

Questa volta inseriamo `2` e verrà quindi creata una istanza di autoavvio al boot chiamata `moonraker-telegram2.service`

Ora apriamo il file di configurazione `telegram_config.sh` dove, oltre ad inserire i dati del secondo bot, c'è da modificare la porta di moonraker al quale si collega. Cambiamo da `7125` a `7126` che è quella che è stata scelta nell'installazione multiprinter. Inoltre, scorrendo in basso, cambiare la porta della webcam sulla stringa `webcam="http://127.0.0.1:8080/?action=snapshot` in `8081`. ora riavviate il servizio o tutta la macchina e dovrestre avere i due bot distinti.

## Configurazioni extra

### Invio notifica temporizzata sullo stato della stampa

Se necessario, quando si è in stampa è possibile inviare una notifica Telegram sullo stato della stampa stessa ogni determinato numero di secondi, basta modificare il parametro `time` sempre all'interno del file `telegram_config.sh` (nell'installazione su singola istanza il file si trova all'interno di /home/pi/klipper_config), nell'esempio seguente il parametro è impostato a 300 secondi, ovvero 5 minuti:

{% raw %}
```
# time in seconds to get an State update. to disable set it to 0
time="300"
```
{% endraw %}

E' anche possibile scegliere se farsi inviare il messaggio di notifica corredato di foto, modificando il valore da `picture="0"` a `picture="1"`

{% raw %}
```
# with picture = 1, without picture = 0
picture="1"
```
{% endraw %}

al termine di qualsiasi modifica è sempre necessario riavviare moonraker-telegram da SSH con il seguente comando (valido solo per il singola istanza, per istanza multipla differisce, quindi si deve inserire il nome fornito all'istanza)

{% raw %}
```
sudo systemctl restart moonraker-telegram
```
{% endraw %}

### Aggiornamento manuale

Per aggiornare manualmente `moonraker-telegram` basta entrare nel path di installazione (es: /home/pi/moonraker-telegram) ed effettuare i seguenti passi

```shell
cd ~/moonraker-telegram
git pull
./scripts/install.sh
```

Rispondere `NO` alla eventuale richiesta di sovrascrittura del file `telegram_config.sh` ed infine riavviare `moonraker-telegram`

```shell
sudo systemctl restart moonraker-telegram
```

### Aggiornamento automatico tramite interfaccia grafica

In uno dei recenti aggiornamenti è stato introdotta la possibilità di aggiornare `moonraker-telegram` direttamente dall'interfaccia grafica di Fluidd o Mainsail.

Dopo aver aggiornato il plugin basta inserire la seguente configurazione all'interno del file `moonraker.conf` (es: /home/pi/klipper_config/moonraker.conf)

{% raw %}
```
[update_manager client moonraker-telegram]
type: git_repo
path: /home/pi/moonraker-telegram ### ATTENZIONE: Questo deve essere il path dove è installato il plugin
origin: https://github.com/Raabi91/moonraker-telegram.git
env: /home/pi/.moonraker-telegram-env/bin/python
requirements: scripts/moonraker-telegram-requirements.txt
install_script: scripts/install.sh
```
{% endraw %}

successivamente riavviare `moonraker-telegram` con il seguente comando

{% raw %}
```
sudo systemctl restart moonraker-telegram
```
{% endraw %}

e infine riavviare `moonraker` con il seguente comando

{% raw %}
```
sudo systemctl restart moonraker
```
{% endraw %}

Se tutti i passi saranno stati effettuati correttamente, apparirà la voce `moonraker-telegram` all'interno dell'update manager della GUI, nell'esempio seguente Fluidd

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/moonraker-telegram-update-manager.png" height="500">
</p>

### Inserimento comandi di controllo/interazione con la Stampante 3D

Tramite il bot Telegram è possibile inviare dei messaggi che effettuano delle azioni/operazioni sulla stampante.

Per poter configurare queste azioni è necessario aprire la chat con @BotFather, inviare il comando `/setcommands`, se si hanno bot multipli, @BotFather chiederà su quale bot impostare i comandi restituendo il seguente messaggio `Choose a bot to change the list of commands.`, quindi selezionare il bot interessato, inserire le seguenti stringhe (devono essere su un singolo messaggio con linee multiple)

{% raw %}
```
state - Sends the current status including a current photo.
pause - Pause current Print.  A confirmation is required
resume - resume current Print.
cancel - Aborts the currently running print. A confirmation is required
help - show list of commands.
print - Will open a file dialog showing the files stored in moonraker. You can select a file to print it.
```
{% endraw %}

 ed inviare il messaggio.

Se tutto è stato impostato correttamente @BotFather risponderà `Success! Command list updated. /help`.

Dal bot configurato per la Stampante sarà possibile interagire con la Stampante 3D stessa tramite moonraker-telegram, inviando uno dei messaggi sopra riportati antecedendo lo `/` (che farà anche l'autocompletamento), gli stessi effettueranno le azioni indicate nelle descrizioni (es: `/state` invia lo stato attuale della stampante comprensivo di foto).

### Verifica processo moonraker-telegram

In caso di problemi, per verificare che il processo `moonraker-telegram` sia funzionante basta digitare da SSH il comando `sudo systemctl status moonraker-telegram.service` che restituirà un output simile al seguente

{% raw %}
```
sudo systemctl status moonraker-telegram.service
● moonraker-telegram.service - moonraker-telegram
   Loaded: loaded (/etc/systemd/system/moonraker-telegram.service; enabled; vendor preset: enabled)
   Active: active (exited) since Tue 2021-04-06 14:01:26 CEST; 1h 31min ago
  Process: 16034 ExecStart=/usr/bin/sh /home/pi/moonraker-telegram/scripts/moonraker-telegram_start.sh & (code=exited, status=0/SUCCESS)
 Main PID: 16034 (code=exited, status=0/SUCCESS)
    Tasks: 5 (limit: 4915)
   CGroup: /system.slice/moonraker-telegram.service
           ├─16042 /home/pi/.moonraker-telegram-env/bin/python /home/pi/moonraker-telegram/scripts/bot.py <your_bot_id> 7125 /home/pi/moonraker-telegram <your_chat_id>
           └─16043 /home/pi/.moonraker-telegram-env/bin/python /home/pi/moonraker-telegram/scripts/websocket-connection-telegram.py 7125 /home/pi/moonraker-telegram

Apr 06 14:01:26 RPi4-3DPrinter systemd[1]: Started moonraker-telegram.
```
{% endraw %}

Se dovesse essere presente un errore di permission simile al seguente:

{% raw %}
```
chmod: changing permissions of '/home/pi/klipper_config/telegram_config.sh': Operation not permitted
```
{% endraw %}

molto probabilmente non sono impostate sul file le permission corrette, quindi verificare con il comando `ls -la /home/pi/klipper_config/telegram_config.sh` le permission del file e se sono `root:root` come da esempio seguente

{% raw %}
```
-rwxrwxrwx 1 root root 1373 Apr  6 14:00 /home/pi/klipper_config/telegram_config.sh
```
{% endraw %}

lanciare il comando `sudo chown pi:pi /home/pi/klipper_config/telegram_config.sh` per modificarle, successivamente verificare che siano state correttamente modificate in `pi:pi` come da esempio seguente

{% raw %}
```
-rwxrwxrwx 1 pi pi 1373 Apr  6 14:00 /home/pi/klipper_config/telegram_config.sh
```
{% endraw %}

Infine riavviare il processo `moonraker-telegram` e verificare nuovamente lo status come indicato sopra.

Se alle voci `<yout_bot_id>` e `<your_chat_id>` sono presenti rispettivamente il bot_id e la chat_id Telegram e il sopra menzionato comando non restituisce degli errori, il plugin dovrebbe funzionare correttamente.

In caso contrario tentare con un riavvio del processo oppure un riavvio del Raspberry Pi, se non dovesse ancora funzionare, rivedere la procedura di installazione/upgrade e le configurazioni all'interno del file `telegram_config.sh` (ricordarsi di procedere a un restart del processo `moonraker-telegram` ad ogni modifica effettuata).
