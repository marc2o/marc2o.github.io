---
layout: article
language: de-DE
image: /images/ubuntu-macbook-img_6532.jpg
title: Aus Alt mach Neu – Aluminium-MacBook 13-Zoll (Unibody, Ende 2008) mit Ubuntu
author: marc2o
abstract: |
  Das MacBook 13-Zoll Aluminium-Unibody (Ende 2008; Modell MacBook5,1) lässt sich mit einer SSD und Ubuntu als Betriebssystem in einen neuen Computer verwandeln.
tags:
- MacBook
- Linux
- Ubuntu
---

Seit Mitte August habe ich meinen neuen Lieblingscomputer. Ein MacBook Air mit M2-Prozessor. Um den Aufbau eines Computermuseums zu vermeiden, mussten alte Rechner weg. Bei meinem Aluminium-MacBook habe ich jedoch den Versuch gewagt, ihm mit Linux neues Leben einzuhauchen.

<!--more-->

Vom [MacBook 13" Unibody](https://everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.0-aluminum-13-late-2008-unibody-specs.html) (Aluminium, Ende 2008) wollte ich mich nicht trennen. Das sieht einfach noch zu schön aus. Außerdem hat es ein optisches Laufwerk). Allerdings ächzt es sehr unter OS X El Capitan (10.11). Trotz der nachträglich eingebauten Crucial MX500 250-GB-SSD vom Typ [CT250MX500SSD1](https://www.crucial.de/ssd/mx500/ct250mx500ssd1) läuft alles in Slow Motion. Von der Fast-Nicht-Verfügbarkeit zeitgenössischer Software mal ganz zu schweigen.

<figure>
<img src="/images/ubuntu-macbook-system-info.png" alt="Ubuntu auf einem MacBook von 2008">
<figcaption>Ubuntu auf meinem alten MacBook5,1</figcaption>
</figure>

## Das richtige Linux für Mac und mich

Es gibt etliche Anleitungen im Netz mit Empfehlungen für ältere Macs. Häufiger allerdings für etwas neuere oder Pro-Modelle. Ich hab 5 verschiedene Linux-Varianten ausprobiert — gut zu laufen und dabei noch gut auszusehen hat am Ende nur eine geschafft.

### Ubuntu LTS 22

Ubuntu in der LTS 22.04.1-Version vereint mehrere Vorzüge:

- Es hat eine tolle Oberfläche.
- Es läuft flüssig und soweit fehlerfrei auf meinem alten MacBook.
- Es hat kompatible Treiber für die Besonderheiten des Modells, wie WLAN und Grafikkarte.

### Update: Zorin OS 16.2 Lite

Nachdem ein Ubuntu-Update meinen Mac funktionsunfähig gemacht hat, habe ich mich nach einer Alternative umgesehen. Bei Reddit bin ich auf [Zorin OS](https://zorin.com/os/) gestoßen, eine Ubuntu-basierte Linux-Distribution. Die Lite-Variante mit XFCE-Desktop soll speziell geeignet sein für bis zu 15 Jahre alte Rechner. Die Installation verläuft analog zu Ubuntu.

## Installation vorbereiten

Zunächst einfach das `.iso`-Image von Ubuntu [herunterladen](https://ubuntu.com/download).

Mit dem [balena Etcher](https://www.balena.io/etcher/) wird nun daraus ein bootfähiger USB-Stick erstellt. Von diesem bootet man das MacBook: dazu beim Einschalten des Macs dann `Alt`- bzw. `Opt`-Taste gedrückt halten und den USB-Stick im Boot-Menü auswählen.

Läuft alles glatt, wird man mit dem Ubuntu-Desktop begrüßt. Hier kann man nun das System ausprobieren oder direkt mit der Installation fortfahren.

## Ubuntu und Software-Treiber installieren

Bei der Installation bin ich den Vorschlägen gefolgt. Außerdem hab ich alles plattgemacht und keine Partition für macOS gelassen.

**Wichtig (aus leidvoller Erfahrung gelernt):** Man erspart sich jede Menge Zeit und Tränen, wenn man das MacBook während der Installation per Kabel mit dem Internet verbindet! Entweder direkt über LAN mit dem Router oder per USB-Kabel mit einem iPhone und dessen mobilen Hotspot.

Nur so werden direkt die zusätzlichen proprietären Wifi-Treiber heruntergeladen. Davon abgesehen scheint der Rechner danach insgesamt besser zu laufen.

Um die manuelle Installation der NVIDIA-Treiber (und Anpassung der Konfiguration) kommt man dennoch nicht herum. Der offizielle Support für die alte GeForce 9400M ist längst eingestellt.

An die Legacy-Treiber für neuere Kernels kommt man über ein spezielles Repository.

```bash
sudo add-apt-repository ppa:kelebek333/nvidia-legacy
sudo apt update
```

Danach lässt sich der Grafikartentreiber im System unter _Zusätzliche Treiber_ aktivieren.

<figure>
<img src="/images/ubuntu-macbook-treiber-installieren.png" alt="Treiber Installieren">
<figcaption>Treiber Installieren</figcaption>
</figure>

Dummerweise lässt sich nun die Helligkeit nicht mehr über die dafür vorgesehenen Heller-/Dunkler-Tasten steuern.

Die Tastensteuerung lässt sich aber über eine Anpassung der zugehörigen X11-Konfiguration wiederherstellen.

Im Verzeichnis `/usr/share/X11/xorg.conf.d/` schaut man nach irgendetwas mit `nvidia*.conf` (der Asterisk `*` ist nur ein Platzhalter für verschiedenste Bezeichnungen, die im Dateinamen enthalten sein können). Dieses Dokument öffnet man und ergänzt im Abschnitt `Device` folgende Optionen:

```toml
Option "NoLogo" "True"
Option "RegistryDwords" "EnableBrightnessControl=1"
```

Schließlich kopiert man diese Datei dann nach `/etc/X11/` (vgl. [ialm](https://askubuntu.com/users/143625/ialm), [Apr 22, 2020 at 3:46](https://askubuntu.com/questions/126441/brightness-controls-doesnt-work-on-a-macbook-pro-5-5-ubuntu-12-04-lts?rq=1#comment2069082_126559) auf askubuntu.com).

## Ubuntu-MacBook im Alltag

Der alte Mac macht mit dem neuen OS deutlich mehr Spaß. Hinzu kommt, dass es ein paar Programme gibt, die tatsächlich wirklich gut gefallen — z. T. besser als vergleichbare Anwendungen in macOS.

Da wäre zum Beispiel [Apostrophe](https://gitlab.gnome.org/World/apostrophe), ein ablenkungsfreier Markdown-Editor. [LibreOffice](https://www.libreoffice.org) ist bei Ubuntu standardmäßig dabei und kann hier sogar Dark-Mode. [Krita](https://krita.org/en/) ist hier ebenfalls schöner als sowohl die Mac- wie auch die Windows-Version. Einzig [Visual Studio Code](https://code.visualstudio.com/docs/setup/linux) ist hier genau das gleiche, wie auf allen anderen Plattformen auch.

## Offene Punkte

Das System läuft stabil und man gewöhnt sich schnell an ggf. etwas andere Tastenkombinationen. Was noch nicht rund läuft ist die Kühlung. Zumindest ist mein Eindruck, dass das Gerät bei in machen Situationen wärmer wird — das kann allerdings auch der alten Hardware geschuldet sein, die nun einfach mehr leisten muss. Aber ich experimentiere noch mit `mpbfan` und `macfanctld`. Updates folgen.

## Update: Zorin OS Lite

Die Installation verläuft genau wie die von Ubuntu selbst. Wichtig ist, genau wie bei Ubuntu selbst, während der Installation per Kabel mit dem Internet verbunden zu sein. So gelingt auch die Installation der Wifi-Treiber.

<figure>
    <figure><img src="/images/zorin_os_img_6745.jpg" alt="Zorin OS auf Unibody-MacBook von 2008 installieren"><figcaption>Installation vom USB-Stick.</figcaption></figure>
    <figure><img src="/images/zorin_os_2023-05-22_18-53-24.png" alt="Zorin OS Welcome-Screen"><figcaption>Begrüßung.</figcaption></figure>
    <figure><img src="/images/zorin_os_2023-05-22_18-57-02.png" alt="Zorin OS Desktop"><figcaption>Sieht gut aus und läuft gut. </figcaption></figure>
</figure>

Der XFCE-Desktop sieht schick aus und läuft auf dem alten MacBook echt gut. In der Lite-Version gibt es nicht so viele Konfigurations­möglichkeiten, aber selbst der Standard-Look kann sich sehen lassen.
