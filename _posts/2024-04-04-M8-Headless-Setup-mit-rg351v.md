---
layout: article
language: de-DE
image: /images/m8-headless-rg351-m8-tracker.jpg
title: M8 Headless mit Teensy 4.1 auf einem Anbernic RG351V
author: marc2o
tags:
- music
- tracker
- teensy
- m8
- anbernic
---

Der _Dirtywave M8 Tracker_ steht schon seit einiger Zeit auf meiner Wunschliste. Leider habe ich immer das Pech, die seltenen und knappen Vorbestellungs­zeitfenster zu verpassen. So auch kürzlich wieder für das neue _Model:02_. Glücklicherweise gibt es die Möglichkeit, den M8 »headless« zu nutzen, also ohne die Original-Hardware.

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

Den Informationen auf Reddit und Discord nach zu urteilen ist die Headless-Konstruktion mit einem RG351 die am besten erprobte. Wegen des Formfaktors habe ich mich für einen RG351V entschieden, so dass es optisch ein wenig einem Game Boy mit LSDJ ähnelt. Für das Gerät spricht, dass Audioqualität gut, die Latenz gering und die Einrichtung ausführlich dokumentiert ist – und man eigentlich nicht viel falsch machen kann[^1].

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

Die Einrichtung des Teensy ist wirklich das einfachste an der ganzen Angelegenheit. Die Headless-Firmware (6) wird mittels der TyTools (7) an das Teensy-Board übertragen. Fertig. Alles musikalische spielt sich dann auf dem Teensy ab. Von dort kommt der Sound, dort sind die Songs gespeichert, die Instrumente, Samples und einfach alles.

Der Einrichtungs&shy;prozess ist ausführlich in [Dirtywave’s M8 Headless Setup](https://github.com/DirtyWave/M8Docs/blob/main/docs/M8HeadlessSetup.md) beschrieben. Ein schneller Test, ob alles korrekt funktioniert ist, kann mit dem Browser-basierten [M8 Display](https://derkyjadex.github.io/M8WebDisplay/)[^2] durchgeführt werden.

Am Mac steht das Board dann fortan als Audio-Input-Device namens _M8_ zur Verfügung. Will man den Sound hören, der vom M8 kommt, so verwendet man entweder eine Audio-Routing-Software oder einfach den QuickTime Player:

1. eine neue Audio-Aufnahme starten,
2. für die Eingabe den M8 auswählen und
3. den Lautstärkeregler verschieben[^3].

<figure>
<img src="/images/m8-headless-rg351-quicktime-player.png" alt="QuickTime Player Audio-Aufnahme">
<figcaption>Der Lautstärkeregler des QuickTime Player – keine Ahnung, warum ich den lange nicht als solchen erkannt habe.</figcaption>
</figure>

Der Teensy wird erstens recht warm und ist zweitens ziemlich nackt. Damit man sich nicht verbrennt und das Board nicht so leicht beschädigt empfiehlt es sich, eine Hülle zu verwenden.

<figure>
<img src="/images/m8-headless-rg351-teensy.jpg" alt="Teensy 4.1 Entwickler-Board in einer GBA Cartridge-Hülle">
<figcaption>Teensy 4.1 Entwickler-Board mit Hülle</figcaption>
</figure>

In Ermangelung eines 3D-Druckers habe ich mir eine Hülle aus einem GBA-Cartridge-Case »geschnitzt«. Die Platine selbst passt exakt in die Hülle, so dass USB-Port und SD-Karte ein Stück rausgucken. Eventuell kommen noch ein paar Löcher für die Belüftung hinzu.

## RG351V

Der RG351V wird mit mindestens einer SD-Karte ausgeliefert. Auf dieser befindet sich das OS. Ich habe sie gelassen wie sie ist und eine neue SD-Karte für die Einrichtung von ArkOS verwendet. Informationen zu ArkOS sowie zur Einrichtung etc. sind in der [ArkOS Wiki](https://github.com/christianhaitian/arkos/wiki) zusammengefasst.

<figure>
<img src="/images/m8-headless-rg351v-arkos.jpg" alt="Anbernic RG351V mit ArkOS">
<figcaption>RG351V mit ArkOS (und eigenem Boot-Bild)</figcaption>
</figure>

Die Anleitung von Jason Porritt – [M8 Headless for RG351 devices](https://github.com/jasonporritt/rg351_m8c) – enthält fast alle Infos, die man braucht, um ein Gerät der RG351-Familie einzurichten. Dem ist wenig hinzuzufügen.

Außer: Die `m8c`-Release v0.1.5 vom 04.11.2022 ist nicht mit der v3.2.x Headless-Firmware kompatibel! Daher sollte unbedingt gleich die neuere Version kopiert werden. – Ob selbst kompilieren auf dem Gerät funktioniert, habe ich nicht probiert.

Der M8-Ordner (8, 9) wird auf der mit ArkOS (10) eingerichteten Karte auf der EasyROMs-Partition im Verzeichnis `ports` abgelegt.

Dann die SD-Karte in den RG351 einlegen und das Gerät einschalten.

Nun muss man sich den Konfigurations-Skripten widmen. Erst die allgemeine Einrichtung mit dem `setup`-Skript (das `setup_pulse`-Skript kann verwendet werden, falls man das Pulse-Audio-System nutzen möchte).

Dann die Buttons mittes `config_m8c_buttons.sh` einrichten. Sind die Buttons eingerichtet, aktiviert man am besten den Remote-Zugriff und macht den Rest am Mac.

```bash
ssh ark@192.168.178.66 #password = ark
pico .local/share/m8c/config.ini
```

Die konfigurierten Buttons können aus der Datei `m8c_config_snippet.txt` herauskopiert werden. Diese befindet sich unter `ports/M8` im selben Verzeichnis wie die Setup-Skripte. Die Standard-Codes für Buttons können in der Dokumentation unter [SDL Game Controller Buttons](https://wiki.libsdl.org/SDL2/SDL_GameControllerButton) nachgelesen werden.

Wer nicht über die Kommandozeile gehen möchte, verwendet z. B. Cyberduck. Neue Verbindung einrichten mit folgenden Daten:

- SFTP
- Server: `192.168.178.66`
- Port: `22`
- Username: `ark`
- Password: `ark`

In den Einstellungen muss die Sichtbarkeit unsichtbarer Dateien aktiviert werden.

Wenn irgendwann alles eingerichtet ist, läuft es tadellos und sieht noch dazu hübsch nerdig aus!

<figure>
<img src="/images/m8-headless-rg351-m8-tracker.jpg" alt="Fertiges M8 Tracker Headless Setup">
<figcaption>Mein fertiges M8-Headless-Setup</figcaption>
</figure>

## Tipps und Tricks

_Die Optionen sind nicht sichtbar_: Wenn die _Options_ auf dem RG351 nicht sichtbar sind, dann ist der Punkt wahrscheinlich bei _Visible Systems_ deaktiviert (zu finden unter _UI Settings_ im Menü, Aufruf mit `[Select]`-Taste)

_Boot-Bild ändern_: Das Boot-Bild im Stammverzeichnis der Boot-Partition kann einfach ersetzt werden. Es muss sich lediglich um eine 24-Bit-BMP-Datei mit 640x480 Pixeln handeln.

_Audio-Glitches oder Verzögerungen_: Die Deaktivierung von Wi-Fi sowie die Verwendung von `M8_Performance` unterbinden die ansonsten möglichen Audio-Glitches.

## Ressourcen

**[Awesome M8](https://github.com/v3rm0n/awesome-m8)**: Auf der Github-Liste gibt es viele Anleitungen, Tutorials und Demos für den M8 Tracker.

**[Laamaa's top sekrit M8 instrument file stash](https://github.com/laamaa/m8i)**: Die Instrument-Dateien von Laamaa auf Github sind eine gute Quelle zum Lernen und Starten eigener Songs.

**[M8 Community SD-Card Starter Pack](https://ia802505.us.archive.org/1/items/ChipmusicResources/)**: Umfangreiches Paket mit Demo-Songs und Samples.

**[Dirtywave Discord](https://discord.gg/WEavjFNYHh)**: Dort gibt es einen unter `#help-me` versteckten `#Headless`-Thread.

[^1]: Nachdem es trotz befolgens aller Schritte nicht funktioniert hat, habe ich mich tatsächlich wundgegooglet, bis ich endlich herausgefunden habe, dass es einer neueren `m8c`-Version bedarf, wenn man die aktuellste Headless-Firmware verwenden möchte.

[^2]: Funktioniert leider weder mit Safari noch mit Firefox. Chrome oder ein Chrome-basierter Browser ist Voraussetzung; z. B. [Ungoogled Chromium für macOS](https://github.com/ungoogled-software/ungoogled-chromium-macos/releases).
[^3]: Ich habe viel zu lange gebraucht, um zu sehen, dass der Lautsprecher standardmäßig stummgeschaltet ist…
