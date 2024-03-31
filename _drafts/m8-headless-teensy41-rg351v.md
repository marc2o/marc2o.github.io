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

Der _Dirtywave M8 Tracker_ steht schon seit einiger Zeit auf meiner Wunschliste. Leider hatte ich immer das Pech, die seltenen und knappen Vorbestellungs­zeitfenster zu verpassen. So auch kürzlich wieder, für das neue _Model:02_. Glücklicherweise gibt es die Möglichkeit, den M8 »headless« zu nutzen, also ohne die Original-Hardware.

<!-- more -->

Der M8 ist ein tragbarer Synthesizer und [Tracker](https://en.wikipedia.org/wiki/Music_tracker)-basierter Sequenzer. Er sieht schick aus, klingt gut und ist definitiv etwas für Chiptune-Enthusiasten wie mich, die mit dem Commodore 64 und Amiga groß geworden sind.

> Powered by the [Teensy](https://www.pjrc.com/teensy/) micro-controller and inspired with love from the renowned Gameboy tracker [Little Sound DJ.](https://www.littlesounddj.com) (dirtywave.com)

Bei der Headless-Variante wird eben dieser Teensy-Mikrocontroller, der auch das Herz des originalen M8 ist, per USB-Kabel mit einem Host verbunden und von dort aus gesteuert.

---

Inhalt:

- [Vorbereitung](#vorbereitung)
- [Teensy](#teensy)
- [RG351V](#rg351v)
- [Tipps und Tricks](#tipps-und-tricks)

---

## Vorbereitung

Den Informationen auf Reddit und Discord nach zu urteilen ist die Headless-Konstruktion mit einem RG351 die am besten erprobte. Die Audioqualität ist gut, die Einrichtung ist leicht und gut dokumentiert und man kann nicht viel falsch machen[^1].

Wegen des Formfaktors habe ich mich für einen RG351V entschieden. Ich hatte selbst nie einen Nintendo Game Boy, aber ich wollte, dass es am Ende optisch dem Game Boy mit LSDJ am nächsten kommt.

### Zutaten

1. 1x Teensy 4.1 Development Board ([LINK](https://www.pjrc.com/store/teensy41.html))
2. 1x ANBERNIC RG351V Handheld Game Console ([LINK](https://anbernic.com/products/anbernic-new-rg351v?variant=40986761298084))
3. 2x microSD-Karte, d. h. je eine für Teensy und RG351 (z. B. SanDisk Ultra 200 GB MicroSDXC)
4. 1x kurzes »USB-C zu Mikro-USB«-Kabel (z. B. [LINK](https://a.aliexpress.com/_EvBSCHX))
5. optional 1x irgendeine Art Hülle als Schutz für das Teensy-Board
6. M8 Headless Firmware für Teensy 4.1 ([LINK](https://github.com/Dirtywave/M8HeadlessFirmware))
7. TyTools zur Installation der Firmware auf dem Teensy ([LINK](https://github.com/Koromix/tytools/releases))
8. M8 Headless für RG351-Geräte ([LINK](https://github.com/jasonporritt/rg351_m8c))
9. Aktuellere Version des `m8c`, die mit der v3.2.x Firmware kompatibel ist ([LINK](https://www.reddit.com/r/RG351/comments/14ruu4t/comment/kiky0it/))
10. ArkOS für RG351 ([LINK](https://github.com/christianhaitian/arkos/wiki), ganz unten in der Liste)
11. balenaEtcher ([LINK](https://etcher.balena.io/))

## Teensy

Die Einrichtung des Teensy ist wirklich das einfachste an der ganzen Angelegenheit. Die Headless-Firmware (6) wird mittels der TyTools an das Teensy-Board übertragen. Fertig. Am Mac steht das Board dann fortan als Audio-Input-Device namens _M8_ zur Verfügung.

Ein schneller Test kann mit dem Browser-basierten [M8 Display](https://derkyjadex.github.io/M8WebDisplay/) durchgeführt werden.

Die Audio-Ausgabe auf dem Mac funktioniert mit dem QuickTime Player. Hierzu …

- eine neue Audio-Aufnahme starten,
- für die Eingabe den M8 auswählen und
- den Lautstärkeregler verschieben[^2].

Der Teensy wird erstens recht warm und ist zweitens ziemlich nackt. Damit man sich nicht verbrennt und das Board nicht so leicht beschädigt empfiehlt es sich, eine Hülle zu verwenden. In Ermangelung eines 3D-Druckers habe ich mir eine Hülle aus einem GBA-Cartridge-Case »geschnitzt«. Die Platine selbst passt exakt in die Hülle, so dass USB-Port und SD-Karte ein Stück rausgucken.

## RG351V

Ich habe die kleinste Version des RG351V bestellt, auch ohne die zusätzliche SD-Karte. Da ich nicht vorhabe, die Konsole für Spiele zu verwenden, benötige ich auch keine zweite Karte. Zumal sämtliche Songs, Instruments etc. auf der SD-Karte im Teensy gespeichert werden. Somit braucht’s für den RG351V nur eine microSD für das Betriebssystem.

Dazu ArkOS (10) herunterladen und mit dem balenaEtcher (11) auf die Karte schreiben. Von der Boot-Partition lässt man die Finger, es sei denn man möchte das Boot-Bild ersetzen. Dieses muss eine 24-Bit-BMP-Datei mit 640x480 Pixeln sein.

Im Verzeichnis `ports` legt man nun den Ordner `M8`ab (8, 9). – Danach die Karte in den RG351V einlegen und einschalten.

### Tipps und Tricks

Wifi deaktivieren und `M8_Performance` verwenden. Oder Pulse-Audio einrichten und verwenden.

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

[^1]: Nachdem es trotz befolgens aller Schritte nicht funktioniert hat, habe ich mich tatsächlich wundgegooglet, bis ich endlich herausgefunden habe, dass es einer neueren `m8c`-Version bedarf, wenn man die aktuellste Headless-Firmware verwenden möchte.

[^2]: Ich habe viel zu lange gebraucht, um zu sehen, dass der Lautsprecher standardmäßig stummgeschaltet ist…
