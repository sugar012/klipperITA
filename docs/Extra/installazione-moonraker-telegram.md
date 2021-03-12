---
layout: default
title: Installazione Moonraker-Telegram
parent: Extra
nav_order: 2
has_children: false
permalink: /extra/installazione-moonraker-telegram/
---

## INSTALLAZIONE MOONRAKER-TELEGRAM

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

Recuperare il numero di chat ID ricercando l'id all'interno dell'oggetto JSON. Nell'esempio seguente la chat ID è `123456789`.

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
               "first_name":"Fungo",
               "last_name":"Cane"
            },
            "chat":{  
               "id":123456789,
               "first_name":"Fungo",
               "last_name":"Cane",
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

## Installare lo script su un Raspberry Pi

Innanzitutto verifica di aver aggiunto la stringa `[display_status]` alla configurazione di klipper. Se già presente non è necessario effettuare operazioni.

Scarica e installa il plugin

se è la prima volta che si procede allo scaricamento del plugin è necessario utilizzare i seguenti comandi SSH

{% raw %}
```
cd
git clone https://github.com/Raabi91/moonraker-telegram
cd moonraker-telegram
```
{% endraw %}

quindi è possibile installare lo script con i seguenti comandi

{% raw %}
```
chmod 755 ./scripts/install.sh
./scripts/install.sh
```
{% endraw %}

durante l'installazione ti verrà richiesto di indicare il percorso contenente il file di configurazione di moonraker. Inserisci il percorso completo. Se hai solo una istanza di moonraker il percorso sarà il seguente 

{% raw %}
```
/home/pi/klipper_config
```
{% endraw %}

verrà anche richiesto se si hanno installazioni multiple. 
Se si ha una sola installazione, basta solo confermare premendo invio. 

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

{% raw %}
```
sudo systemctl restart moonraker-telegram
```
{% endraw %}

Se è stato fatto tutto a dovere, all'avvio di una stampa verrà inviata una notifica su Telegram all'interno del proprio bot.

## Configurazioni extra

Se necessario è possibile inviare una notifica Telegram ogni determinato numero di secondi modificando il parametro `time` sempre all'interno del file `telegram_config.sh` (nell'esempio seguente impostata a 900 secondi, quindi 15 minuti):

{% raw %}
```
# time in seconds to get an State update. to disable set it to 0
time="900"
```
{% endraw %}

al termine di qualsiasi modifica è sempre necessario riavviare moonraker-telegram da SSH con il seguente comando

{% raw %}
```
sudo systemctl restart moonraker-telegram
```
{% endraw %}
