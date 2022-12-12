---
layout: article
language: de-DE
image: IMG_6369.jpg
title: Aus Alt mach Neu – Wie ich mein altes Aluminium-MacBook (Unibody, Ende 2008) mit Ubuntu wieder fit gemacht hab
author: marc2o
abstract: |
  Das MacBook Aluminium Unibody (Ende 2008; Modell MacBook5,1) lässt sich mit einer SSD und Ubuntu als Betriebssystem in einen neuen Computer verwandeln.
tags:
- MacBook
- Linux
- Ubuntu
---

Seit Mitte August habe ich meinen neuen Lieblingscomputer, ein MacBook Air mit M2-Prozessor. Um den Aufbau eines Computermuseums zu vermeiden, mussten die alten Rechner weg. Einzig vom [MacBook 13" Unibody](https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.0-aluminum-13-late-2008-unibody-specs.html) (Aluminium, Ende 2008) wollte ich mich nicht trennen.  Das sieht einfach noch zu schön aus.

Allerdings ächzt es sehr unter OS X El Capitan (10.11). Trotz der nachträglich eingebauten Crucial MX500 250-GB-SSD vom Typ [CT250MX500SSD1](https://www.crucial.de/ssd/mx500/ct250mx500ssd1) läuft alles wie in Slow Motion. Von der Nicht-Verfügbarkeit zeitgenössischer Software mal ganz zu schweigen.

Jetzt habe ich den Versuch gewagt, meinem alten MacBook neues Leben einzuhauchen: mit Linux.


## Das richtige Linux für Mac und mich

Es gibt etliche Anleitungen im Netz mit Empfehlungen ältere Macs. Meist allerdings für etwas neuere oder Pro-Modell. Ich hab zig Linux-Varianten ausprobiert — richtig gelaufen ist und gut ausgesehen hat nur eine.

### Ubuntu LTS 22

Ubuntu in der LTS 22.04.1-Version vereint mehrere Vorzüge:

- Es hat eine tolle Oberfläche
- Es läuft gut und schnell auf meinem alten MacBook
- Es hat kompatible Treiber für die besonderheiten des Modells


## Ubuntu und Software-Treiber installieren

Zunächst einfach das `.iso`-Image von Ubuntu [herunterladen](https://ubuntu.com/download).

Mit dem [balena Etcher](https://www.balena.io/etcher/) wird nun daraus ein bootfähiger USB-Stick erstellt. Von diesem bootet man das MacBook: dazu beim Einschalten des Macs dann `Alt`- bzw. `Opt`-Taste gedrückt halten und den USB-Stick im Boot-Menü auswählen.

### Wifi

**Wichtig (aus leidvoller Erfahrung gelernt):** Man erspart sich jede Menge Zeit und Tränen, wenn man das MacBook während der Installation per Kabel mit dem Internet verbindet!

Entweder direkt über LAN mit dem Router oder per USB-Kabel mit einem iPhone und dessen mobilen Hotspot. Nur so werden direkt die zusätzlichen proprietären Wifi-Treiber heruntergeladen.  Davon abgesehen scheint der Rechner danach insgesamt besser zu laufen.

### Grafikkarte

Um die manuelle Installation der NVIDIA-Treiber kommt man dennoch nicht herum. Der offizielle Support für die alte GeForce 9400M ist längst eingestellt.

An die Legacy-Treiber für neuere Kernels kommt man über ein spezielles Repository.

```bash
sudo add-apt-repository ppa:kelebek333/nvidia-legacy
sudo apt update
```

Danach lässt sich der Grafikartentreiber im System unter _Zusätzliche Treiber_ aktivieren.

![Treiber Installieren](../images/ubuntu-macbook-treiber-installieren.png)
Dummerweise lässt sich nun die Helligkeit nicht mehr über die dafür vorgesehenen Heller-/Dunkler-Tasten steuern.

Die Tastensteuerung lässt sich aber über eine Anpassung der zugehörigen X11-Konfiguration wiederherstellen.

Im Verzeichnis `/usr/share/X11/xorg.conf.d/` schaut man nach irgendetwas mit `nvidia*.conf` (der Asterisk `*` ist nur ein Platzhalter für verschiedenste Bezeichnungen, die im Dateinamen enthalten sein können). Dieses Dokument öffnet man und ergänzt im Abschnitt `Device` folgende Optionen:

```config
Option "NoLogo" "True"
Option "RegistryDwords" "EnableBrightnessControl=1"
```

Schließlich kopiert man diese Datei dann nach `/etc/X11/` (vgl. [ialm](https://askubuntu.com/users/143625/ialm), [Apr 22, 2020 at 3:46](https://askubuntu.com/questions/126441/brightness-controls-doesnt-work-on-a-macbook-pro-5-5-ubuntu-12-04-lts?rq=1#comment2069082_126559) auf askubuntu.com).


## Software

…
