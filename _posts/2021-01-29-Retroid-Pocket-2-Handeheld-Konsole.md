---
layout: article
language: de-DE
image: /images/rp2-foto-4.jpg
title: Retroid Pocket 2 Handheld-Konsole
author: marc2o
date: 2021-01-29
tags:
- retroid pocket 2
- gaming
- handheld
- spielkonsole
---

Meine Konsolensammlung wächst. Letzter Neuzugang: Der [Retroid Pocket 2](https://www.goretroid.com) ist eine Handheld-Spielkonsole aus China. Ich hab die Variante »Retro« im Gameboy-Design gewählt, und ich muss sagen: Das Ding sieht super aus und fühlt sich noch besser an.

<!--more-->

Auf der dual-boot-fähigen Konsole läuft wahlweise Android 6 bzw. 8.1 (nach Upgrade) oder das eigene  RetroidOS. Während letzteres heißt, dass direkt ein einen Multi-Plattform-Emulator gebootet wird, hat man unter Android Zugriff auf verschiedene Emulatoren, allen voran natürlich RetroArch und ScummVM. 

Für mich ist die Konsole momentan einfach die schönste Möglichkeit, meine Lieblings-Spiele vom NES, SNES und Mega Drive wieder zu erleben.

<figure>
    <figure><img src="/images/rp2-foto-1.jpg" alt="Retroid Pocket 2 Konsole"><figcaption>Formschön.</figcaption></figure>
    <figure><img src="/images/rp2-foto-2.jpg" alt="Retroid Pocket 2 Konsole"><figcaption>Die Buttons fühlen sich gut an.</figcaption></figure>
    <figure><img src="/images/rp2-foto-3.jpg" alt="Retroid Pocket 2 Konsole"><figcaption>Liegt gut in der Hand. </figcaption></figure>
    <figure><img src="/images/rp2-foto-4.jpg" alt="Retroid Pocket 2 Konsole"><figcaption>Funktioniert.</figcaption></figure>
</figure>


## Einrichtung, Benutzung und Optimierung

### Ganz allgemein

In der Toolbox-App:

- Das Häkchen bei »Clean background processes when standby enabled« und »Allow clean foreground processes« setzen 
- Die Obergrenze der Hintergrundprozesse bei »Background process limit« auf »0 (no background processes)« setzen

### RetroArch konfigurieren

In **RetroArch** (die Version mit dem Space Invaders–Icon) muss bei einigen Playstation-Spielen, wie z. B. *Legend of Mana*, muss unter *Options* der Controller-Typ (*Pad Type*) für Player 1 auf *analog* gesetzt werden.

Außerdem lohnt es sich, bei reinen Gameboy-Spielen für den Core die Darstellungsoptionen etwas anzupassen. Besonders gut sieht es aus, wenn man unter *Options* die folgenden Einstellungen (als *Content Directory Override*) verwendet:

- GB Colorization: auto
- Internal Palette: SGB – 4H
- Color Correction: GBC only

RetroArch und Emulations-Kerne:

- Die RetroArch-Version für den RP2: [Retroarch-1-8-4_git-release](https://www.apkmirror.com/apk/libretro/retroarch/retroarch-1-8-4_git-release/)
- Die RetroArch Stock-Cores für den RP2: [Archiv (RAR)](https://drive.google.com/file/d/1_MPYLoE6cpAGaZgmR99qtVl29Gehf_dv/view)
- Version 1.9.0 (nicht 64-Bit!): [https://buildbot.libretro.com/stable/1.9.0/android/](https://buildbot.libretro.com/stable/1.9.0/android/)
- Emulation Cores: [http://buildbot.libretro.com/nightly/android/latest/armeabi-v7a/](http://buildbot.libretro.com/nightly/android/latest/armeabi-v7a/)

### My Boy konfigurieren

Bei **My Boy** habe ich die bei den *Video Settings* die Option *Stretch to fit screen* angewählt und das *Linear filtering* deaktiviert. Unter *Input* legt man am besten den Aufruf des Menüs auf die L2-Taste und *Fast forward* auf R2. Das *Virtual keypad* natürlich deaktiveren.

### Weitere Tipps und Anleitungen

- Wagner’s Tech Talk [Retroid Pocket 2 Tips](http://wagnerstechtalk.com/retroidp2/)
- Reddit [RP2 Android 8.1 Reset Collection & Retroarch Setup](https://www.reddit.com/r/retroid/comments/jp2s9r/rp2_android_81_reset_collection_retroarch_setup/)
- Eigenen Screen-Protector machen: [A tutorial on how to make your own screen protector for Retroid Pocket 2](https://youtu.be/1f4VvxRQUkA)
- RetroArch-Besonderheiten: [A Brief Guide to RetroArch](https://wiki.retroidhandhelds.com/index.php?title=A_Brief_Guide_to_Retroarch)
- DraStic DS Emulator: [Retroid Pocket 2 Nintendo DS Guide](https://retrogamecorps.com/2020/09/22/guide-nintendo-ds-on-the-retroid-pocket-2/)


## Firmware-Upgrade auf Android 8.1 (v3)

Das erste Upgrade auf 8.1 war noch umständlich und hat leider auch viele Fehler gehabt. Zum Beispiel waren bei RetroArch die Achsen des linken Analog-Sticks invertiert. Um dies zu beheben, musste die **Gamepad Mode Settings** App gestartet und die Option **Use Circular Joystick Track** angehakt werden — und zwar nach jedem Systemstart.

Aber seit Januar 2021 ist ein neues Android 8.1-Update »v3« verfügbar:

- [https://wiki.retroidhandhelds.com/index.php?title=Firmware](https://wiki.retroidhandhelds.com/index.php?title=Firmware)
- [https://drive.google.com/drive/folders/1pSDVxLSOLqMirmPENWf2sdxrDKfOLd6z](https://drive.google.com/drive/folders/1pSDVxLSOLqMirmPENWf2sdxrDKfOLd6z)

Ein Leitfaden zur Installation liegt bei. Eine schönere Dokumentation gibt es bei Retro Game Corps: [Retroid Pocket 2 Android 8.1 Install Guide](https://retrogamecorps.com/2020/12/29/retroid-pocket-2-android-8-1-install-guide/).


## Alternative-Firmware: LineageOS

Diese inoffizielle Version von LineageOS 15.1 ist eine Alternative für das reguläre Android 8.1. Besonders die Oberfläche läuft besser und der App-Launcher RePoLa ist standardmäßig eingerichtet. 

Alle Details unter [»LineageOS on Retroid Pocket 2«](https://retrogamecorps.com/2021/03/21/lineageos-android-8-1-on-retroid-pocket-2/).

Eine gute Anleitung zum Upgrade auf LineageOS 15.1 ist dieses Video: https://www.youtube.com/watch?v=SCJpCgBJDfg von Retro Game Corps.


## Familienanschluss

Auch wenn das Gerät durchaus umstritten ist, gerade was die technischen Spezifikationen angeht, so gibt es doch eine lebendige Fan-Gemeinde. Regelmäßige Infos, Tipps und Neuigkeiten werden hier veröffentlicht:

- Discord: [https://discord.com/invite/mnA2Ju2RZy](https://discord.com/invite/mnA2Ju2RZy)
- Reddit: [https://www.reddit.com/r/retroid/](https://www.reddit.com/r/retroid/)


## Kosmetische Eingriffe

Ich nutze meinen RP2 ausschließlich mit Android, und das sieht im Standard leider nicht sonderlich konsolenmäßig aus. Aber das lässt sich glücklicherweise anpassen.

Als erstes: Das Wallpaper! Fans haben für den RP2 eine eigene Website für Hintergrundbilder erstellt. Diese kann auch direkt im RP2-Browser aufgerufen werden.

- Wallpapers: [http://gallery.retroidhandhelds.com](http://gallery.retroidhandhelds.com)

Zweitens, der Launcher! Es gibt für Android eine Reihe von alternativen Launchern, die weniger nach Smartphone aussehen, weil sie z. B. für TV-Geräte gedacht sind. Mein Favorit ist **RePoLa**, mit dem der RP2 schon nicht mehr so sehr nach Handy aussieht.

- GitHub: [https://github.com/sreichholf/repola](https://github.com/sreichholf/repola)

Drittens, wenn man auch noch ein allgemeines Emulator-Frontend benutzen möchte, um nicht mehr jeden Emu einzeln zu starten: **Retro Mega**, ein [Pegasus](https://pegasus-frontend.org)-Theme, speziell für den RP2:

- GitHub: [https://github.com/djfumberger/retromega](https://github.com/djfumberger/retromega)


## DIY und Reparatur

Seit kurzem gibt es auch eine offizielle Seite, auf der man Ersatzteile bestellen kann, von Buttons bis zur Schale.

- RETROID: [https://www.goretroid.com/collections/diy](https://www.goretroid.com/collections/diy)


## Probleme beheben

### RetroArch: Favoriten lassen sich nicht speichern

Wenn sich in in RetroArch Spiele nicht zu den Favoriten hinzufügen lassen (und dies auch nicht funktioniert, während das Spiel geöffnet, also der Core geladen ist) und die Historie nicht gespeichert wird, dann liegt es möglicherweise an fehlenden Schreibberechtigungen für die entsprechenden Listendateien.

Dieses Problem lässt sich durch anpassen der Pfade in der Konfigurations-Datei beheben.

Die Konfiguration ist in der `retroarch.cfg`-Datei gespeichert. Diese befindet sich hier:

```
/Internal shared storage/Android/data/com.retroarch/files/retroarch.cfg
```

Dann die Pfade für Historie und Favoriten anpassen und z. B. auf die SD-Karte lenken.

```
content_history_path = "/storage/sdcard1/RetroArch/content_history.lpl"
content_favorites_path = "/storage/sdcard1/RetroArch/content_favorites.lpl"
```

Die Lösung stammt von [JFCG4mer auf Reddit](https://www.reddit.com/r/retroid/comments/kqzu3c/comment/gi7avz2/?utm_source=share&utm_medium=web2x&context=3).


## Nicht nur Emulation

Am meisten hat mich persönlich gefreut, dass mein heißgeliebter [**Shovel Knight**](https://yachtclubgames.com/shovel-knight/) tadellos auf dem RP2 läuft! Aber auch [**Evoland II**](https://evoland.shirogames.com) läuft prima und ist super süß.
