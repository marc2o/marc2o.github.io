---
layout: article
language: de-DE
image: IMG_6369.jpg
title: Aus Alt mach Neu – Wie ich mein altes MacBook 13" (Aluminum, late 2008) mit Ubuntu 22.04 wieder fit gemacht hab
author: marc2o
tags:
- MacBook
- Linux
- Ubuntu
---


Seit Mitte August habe ich mein neues MacBook Air mit M2-Prozessor. Um den Aufbau eines Computermuseums zu vermeiden, habe ich das MacBook Air (early 2015) in Zahlung gegeben und das alte, vergilbt-weiße 2006er MacBook kommt einfach weg.

Nur vom MacBook 13" Aluminium (late 2008) wollte ich mich nicht trennen. Das sieht einfach noch zu schön aus. Es ächzt allerdings unter Mac OS X und fühlt sich an wie ein Slow-Motion-Computer. Außerdem wurde es immer schwieriger, zeitgenössische Anwendungen zu nutzen.

Die nachträglich eingebaute Crucial MX500 250-GB-SSD vom Typ [CT250MX500SSD1](https://www.crucial.de/ssd/mx500/ct250mx500ssd1) hatte schon wieder ein bisschen Geschwindigkeit aus dem alten Laptop herausgekitzelt. Jetzt wollte ich den Versuch wagen, meinem alten MacBook neues Leben einzuhauchen: mit Linux.


## Das richtige Linux für Mac und mich

Die im Internet zu findenden Empfehlungen für alte Macs — Linux Mit, Xubuntu, Ubuntu Budgie — habe ich alle probiert. Entweder war die Oberfläche hässlich oder es ist nicht gut gelaufen.

Am besten hat mir von Anfang an [Ubuntu](https://ubuntu.com/download) in der LTS 22.04.1-Version gefallen. Tolle Benutzeroberfläche und es hat schon beim Probelauf einfach funktioniert.


## Installieren

Zuerst mit dem [balena Etcher](https://www.balena.io/etcher/) aus dem `.iso`-Image einen bootfähigen USB-Stick erstellen. Von diesem bootet man das MacBook. Einfach beim Einschalten des Macs dann `Alt`- bzw. `Opt`-Taste gedrückt halten und den USB-Stick im Boot-Menü auswählen.

Jetzt probiert man Ubuntu entweder einfach erstmal aus oder beginnt direkt die Installation.

**Wichtig (aus leidvoller Erfahrung gelernt):** Man erspart sich jede Menge Zeit und Tränen, wenn man das MacBook während der Installation per Kabel mit dem Internet verbindet! Oder meinetwegen auch per USB-Kabel mit dem Handy und so den mobilen Hotspot benutzt. Nur so werden direkt die zusätzlichen proprietären Treiber heruntergeladen. Dann funktioniert auch direkt Wifi und insgesamt scheint der Rechner besser zu laufen.


## Die Grafikarte

Um die manuelle Installation der NVIDIA-Treiber kommt man dennoch nicht herum. Der Support für die alte GeForce 9400M ist längst eingestellt.

Um an die Legacy-Treiber für neuere Kernels heranzukommen, muss das folgende Repository hinzugefügt werden.

```bash
sudo add-apt-repository ppa:kelebek333/nvidia-legacy
sudo apt update
```

Danach lässt sich der Grafikartentreiber unter _Zusätzliche Treiber_ aktivieren.

![Treiber Installieren](ubuntu-macbook-treiber-installieren.png)

Dummerweise lässt sich nun die Helligkeit nicht mehr über die dafür vorgesehenen Heller-/Dunkler-Tasten steuern. Damit das wieder geht, ist es nötig, die zugehörige X11-Konfiguration anzupassen.

Im Verzeichnis `/usr/share/X11/xorg.conf.d/` schaut man nach irgendetwas mit `nvidia*.conf`. Dieses Dokument öffnet man und ergänzt unter `Device` folgende Optionen:

```config
Option "NoLogo" "True"
Option "RegistryDwords" "EnableBrightnessControl=1"
```

Schließlich kopiert man diese Datei dann nach `/etc/X11/` (vgl. [ialm](https://askubuntu.com/users/143625/ialm), [Apr 22, 2020 at 3:46](https://askubuntu.com/questions/126441/brightness-controls-doesnt-work-on-a-macbook-pro-5-5-ubuntu-12-04-lts?rq=1#comment2069082_126559) auf askubuntu.com).

## Software

…
