---
layout: default
title: Installazione Multicam
nav_order: 12
has_children: false
permalink: /installazione-multicam/
---

{% include breadcrumbs.html %}

## INSTALLAZIONE MULTICAM


Per poter utilizzare due o più webcam con MJPG-Streamer ,avendo seguito la [guida](https://sugar012.github.io/klipperITA/docs/webcam.html#installazione-webcam), basta aggiungere un altra coppia di scripts per l'avvio automatico nella cartella scripts.

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
