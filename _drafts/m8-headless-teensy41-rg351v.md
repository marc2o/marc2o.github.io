---
layout: article
language: de-DE
image: /images/...
title: M8 Headless mit Teensy 4.1 auf einem Anbernic RG351V
author: marc2o
tags:
- music
- tracker
- teensy
- m8
- anbernic
---

Der _Dirtywave M8 Tracker_ steht schon seit ein, zwei Jahren auf meiner Wunschliste. Aber leider hatte ich immer das Pech, die knappen Vorbestellungs­zeitfenster zu verpassen. Wie auch kürzlich wieder für das neue _Model:02_. Glücklicherweise gibt es die Möglichkeit, den M8 »headless« zu nutzen.

<!-- more -->

Der M8 ist ein tragbarer Synthesizer und [Tracker](https://en.wikipedia.org/wiki/Music_tracker)-basierter Sequenzer für unterwegs.

> Powered by the [Teensy](https://www.pjrc.com/teensy/) micro-controller and inspired with love from the renowned Gameboy tracker [Little Sound DJ.](https://www.littlesounddj.com) (dirtywave.com)

Bei der Headless-Variante wird der Teensy, der auch das Herz des originalen M8 ist, per USB-Kabel mit einem Host-Computer verbunden und von dort aus gesteuert.

---

Inhalt:

- [Vorbereitung](#vorbereitung)
- [Teensy](#teensy)
- [RG351V](#rg351v)

---

## Vorbereitung

Den Informationen auf Reddit und Discord nach zu urteilen ist die Headless-Konstruktion mit dem RG351 die am besten erprobte. Die Audioqualität ist gut, die Einrichtung ist leicht und gut dokumentiert und man kann nicht viel falsch machen (bis auf eines, aber dazu komme ich noch).

Hardware:

- Teensy 4.1 Development Board ([LINK](https://www.pjrc.com/store/teensy41.html))
- ANBERNIC RG351V Handheld Game Console ([LINK](https://anbernic.com/products/anbernic-new-rg351v?variant=40986761298084))
- je eine microSD-Karte für Teensy und RG351 (z. B. SanDisk Ultra 200 GB MicroSDXC)
- kurzes »USB-C zu Mikro-USB«-Kabel (z. B. [LINK](https://a.aliexpress.com/_EvBSCHX))
- irgend eine Art Hülle als Schutz für den Teensy (ich hab mir eine aus einem GBA Cartridge Case gebastelt)

Software:

- M8 Headless Firmware für Teensy 4.1 ([LINK](https://github.com/Dirtywave/M8HeadlessFirmware))
- TyTools zur Installation der Firmware auf dem Teensy ([LINK](https://github.com/Koromix/tytools/releases))
- M8 Headless für RG351-Geräte ([LINK](https://github.com/jasonporritt/rg351_m8c))
- Aktuellere Version des `m8c` für die 3.2.x Firmware ([LINK](https://www.reddit.com/r/RG351/comments/14ruu4t/comment/kiky0it/))
- ArkOS für RG351 ([LINK](https://github.com/christianhaitian/arkos/wiki), ganz unten in der Liste)
- balenaEtcher ([LINK](https://etcher.balena.io/))

## Teensy

…

## RG351V

Wifi deaktivieren und `M8_Performance` verwenden. Oder Pulse-Audio einrichten und verwenden.

### Remote Access

`ssh ark@192.168.178.66` mit Passwort `ark`

`config.ini` in `.local/share/m8c`

`config_m8c_buttons.sh` aus `m8c_config_snippet.txt` kopieren

SDL Game Controller Buttons:

https://wiki.libsdl.org/SDL2/SDL_GameControllerButton


Cyberduck:

- SFTP
- Server: `192.168.178.66`
- Port: `22`
- Username: `ark`
- Password: `ark`
