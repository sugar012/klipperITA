---
layout: default
title: Installazione Webcam
parent: Extra
nav_order: 1
has_children: false
permalink: /extra/installazione-webcam/
---

# Installazione Webcam
{: .fw-400 }

ATTENZIONE: Nei seguenti pezzi di codice di esempio sotituire sempre `TUOUSER` con il proprio username

Da terminale inviare uno alla volta:

```shell
cd ~
sudo apt install subversion libjpeg8-dev imagemagick ffmpeg libv4l-dev cmake
git clone https://github.com/jacksonliam/mjpg-streamer.git
cd mjpg-streamer/mjpg-streamer-experimental
export LD_LIBRARY_PATH=.
make
```

Testiamo lo stream di mjpg streamer:

```shell
sudo ./mjpg_streamer -i "./input_uvc.so" -o "./output_http.so"
```


Creaiamo lo script di avvio automatico (non usare sudo):

```shell
cd ~
mkdir scripts
nano ~/scripts/webcam
```

```
#!/bin/bash
# Start / stop streamer daemon

case "$1" in
    start)
        /home/TUOUSER/scripts/webcamDaemon >/dev/null 2>&1 &
        echo "$0: started"
        ;;
    stop)
        pkill -x webcamDaemon
        pkill -x mjpg_streamer
        echo "$0: stopped"
        ;;
    *)
        echo "Usage: $0 {start|stop}" >&2
        ;;
esac
```

Creaiamo lo script demone dello stream (non usare sudo):

```shell
nano ~/scripts/webcamDaemon
```
```
#!/bin/bash

MJPGSTREAMER_HOME=/home/TUOUSER/mjpg-streamer/mjpg-streamer-experimental
MJPGSTREAMER_INPUT_USB="input_uvc.so"
MJPGSTREAMER_INPUT_RASPICAM="input_raspicam.so"

# init configuration
camera="auto"
camera_usb_options="-r 640x480 -f 10"
camera_raspi_options="-fps 10"

if [ -e "/boot/octopi.txt" ]; then
    source "/boot/octopi.txt"
fi

# runs MJPG Streamer, using the provided input plugin + configuration
function runMjpgStreamer {
    input=$1
    pushd $MJPGSTREAMER_HOME
    echo Running ./mjpg_streamer -o "output_http.so -w ./www" -i "$input"
    LD_LIBRARY_PATH=. ./mjpg_streamer -o "output_http.so -w ./www" -i "$input"
    popd
}

# starts up the RasPiCam
function startRaspi {
    logger "Starting Raspberry Pi camera"
    runMjpgStreamer "$MJPGSTREAMER_INPUT_RASPICAM $camera_raspi_options"
}

# starts up the USB webcam
function startUsb {
    logger "Starting USB webcam"
    runMjpgStreamer "$MJPGSTREAMER_INPUT_USB $camera_usb_options"
}

# we need this to prevent the later calls to vcgencmd from blocking
# I have no idea why, but that's how it is...
vcgencmd version

# echo configuration
echo camera: $camera
echo usb options: $camera_usb_options
echo raspi options: $camera_raspi_options

# keep mjpg streamer running if some camera is attached
while true; do
    if [ -e "/dev/video0" ] && { [ "$camera" = "auto" ] || [ "$camera" = "usb" ] ; }; then
        startUsb
    elif [ "`vcgencmd get_camera`" = "supported=1 detected=1" ] && { [ "$camera" = "auto" ] || [ "$camera" = "raspi" ] ; }; then
        startRaspi
    fi

    sleep 120
done
```
Salviamo il documento con `CTRL+X`

In nello script è possibile aggiustare risoluzione e framerate semplicemente editando i valori nella riga `camera_usb_options`.

Si consiglia di non esagerare con la risoluzione e il framerate perchè molto dipendono dal vostro sistema/rete. Per stare conservativi e avere buona fluidità rimanere al messimo a 720p e 15/20fps.


Editiamo i permessi dei file di startup:

```shell
chmod +x ~/scripts/webcam
chmod +x ~/scripts/webcamDaemon
```

Aggiungiamo `webcam` allo startup:

```shell
sudo nano /etc/rc.local
```


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/home/TUOUSER/scripts/webcam start

exit 0
```
Salviamo il documento con `CTRL+X`

Start webcam:
```shell
sudo ~/scripts/webcam start
```

Cambiamo i permessi di `rc.local`:
```shell
sudo chmod +x /etc/rc.local
```

Il link da inserire nell'interfaccia web (`UI SETTINGS` in fluidd) sarà quindi http://VOSTRO-IP:8080/?action=stream

<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/image33.png" height="450">
</p>
