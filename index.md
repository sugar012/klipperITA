---
layout: default
title: Benvenuto
tagline: Documentazione in Italiano per l'installazione del Firmware Klipper, Mainsail, Fluidd, Kiauh, Webcam, Stampante 3D
description: Documentazione in Italiano per l'installazione del Firmware Klipper, Moonraker, Mainsail, Fluidd e altri componenti per Stampanti 3D
nav_order: 1
has_children: false
---

# Guida Installazione Klipper e altri Componenti
{: .fw-400 }


<p align="center">
<img src="https://raw.githubusercontent.com/sugar012/klipperITA/main/images/klipper-logo-it.png" height="350">
</p>


*La guida è in continuo aggiornamento, è possibile verificare la data di ultima modifica in fondo ad ogni singola pagina, dove è presente `Utima modifica del GG/MM/AAAA alle ore HH:MM`.*

## Prefazione

Klipper è un firmware per Stampante 3D che combina la potenza di un computer generico con uno o più microcontrollori (ovvero le board delle Stampanti 3D).

Al seguente link (in Inglese) è possibile visionare le [Caratteristiche di Klipper](https://www.klipper3d.org/Features.html){:target="_blank"}

🟥**IMPORTANTE**: Al seguente link (**DA VISIONARE ATTENTAMENTE**) i [PREREQUISITI](https://klipper-italia.xyz/prerequisiti/){:target="_blank"} per poter installare Klipper e relativi componenti oggetto di questa guida.

## Introduzione Guida

Questa guida in Italiano ricopre tutti i passi base per poter installare il firmware Klipper e altri componenti sulla propria Stampante 3D (se la board è supportata) in modo da avere, al termine di tutti i passi un'installazione completa e funzionante. Data la varietà di singoli Hardware e Sistemi Operativi ad oggi presenti sul mercato, la guida per il momento ricopre per buona parte l'installazione su Hardware Raspberry Pi con Sistema Operativo Raspberry Pi OS (ex Raspbian).

**Se si utilizza Hardware diverso da Raspberry Pi oppure Sistemi Operativi diversi da Raspberry Pi OS (ex Raspbian), alcuni comandi e/o configurazioni potrebbero differire.**

**Installare questo firmware richiede un minimo di manualità con Linux e soprattutto con l’uso di un motore di ricerca (es: Google), noi ci siamo impegnati a rendere la guida il più semplice possibile ma procedere a proprio rischio e leggere attentamente prima di acquistare un Raspberry Pi, che è il sistema [SBC](https://en.wikipedia.org/wiki/Single-board_computer){:target="_blank"} sulla quale sono basati i comandi e le configurazioni presenti in questa guida.**

Klipper è un firmware che, sfruttando la potenza di calcolo di un Raspberry Pi/PC Linux o derivati, riesce ad eseguire algoritmi complessi per il calcolo della cinematica offrendo inoltre la possibilità di raggiungere step rate più elevati.

A differenza di Marlin, che gira sulla scheda della stampante ed è quindi limitato dalla potenza di calcolo di quest'ultima, Klipper gira sul Raspberry Pi, esegue tutti i calcoli e invia le istruzioni alla scheda della stampante (anch'essa flashata con klipper per permettere la comunicazione) che deve solo eseguirli inviando i comandi ai motori/attuatori.

Un'altra particolarità di questo firmware è la sua compatibilità con diverse interfacce web, potremo infatti scegliere tra 4 alternative: **Fluidd**, **Mainsail**, **OctoPrint** e **DuetWebControl 2**.
Queste, oltre ad essere graficamente belle e curate, vanno a sostituire o affiancare lo schermo della stampante e sarà quindi più semplice gestire tutto con mouse e tastiera, tablet/smartphone o qualsiasi dispositivo che abbia un browser!

Tra gli altri vantaggi di Klipper troviamo la possibilità di essere modificato senza alcuna compilazione: tramite l'interfaccia web è infatti possibile accedere al file di configurazione `printer.cfg` e modificarlo al volo. Basterà salvare e fare un restart del firmware et voilà!

Vi dimenticherete di visual studio e di quelle mille righe di codice da scorrere ogni volta. Su klipper il `printer.cfg` funziona al contrario di Marlin: si parte da un file vuoto a cui andremo ad aggiungere funzioni dalla documentazione solo se ci interessano, questo rende più facile e veloce la configurazione.
