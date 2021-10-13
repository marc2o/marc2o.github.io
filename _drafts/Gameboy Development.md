---
layout: article
language: de-DE
image: /images/...
title: Spiele entwickeln für den Nintendo Game Boy
author: marc2o
tags:
- spiele
- entwickelung
- nintendo
- game boy
- mac
---

Mit den Spielen, die man heute so »retro« nennt, bin ich aufgewachsen. Daher habe ich zu alten Computern und Konsolen ein besonderes Verhältnis. Ich mag die besonderen Einschränkungen der alten Systeme und die Kreativitt, die es erfordert, trotz dieser Einschränkungen etwas zu bewerkstelligen, das Spaß macht und gut aussieht. Dass ich damit nicht allein bin zeigt die Aktivität der Homebrew-Szene — wie viele Spiele und Demos immer noch beispielsweise für den Game Boy und Game Boy Color entwickelt werden, begeistert mich (z. B. [GB Compo 2021](https://itch.io/jam/gbcompo21)).


Weil ich das zu gern mal selbst ausprobieren möchte (etwas ähnliches habe ich schon für den Atari 2600 probiert), habe ich hier eine Übersicht it Tipps und Links zusammengestellt (eher für mich, als persönliche Link-Sammlung).


## Spiele entwickeln für den Game Boy und Game Boy Color

Als erstes gilt es, die richtigen Werkzeuge für die Entwicklung zu wählen. Das ist wichtig, denn davon hängt ab, wie viel Arbeit das geplante Spiel machen wird, was möglich sein wird und wie schnell das Spiel läuft.

Erläuterungen dazu gibt es hier im Leitfaden [**Choosing tools for Game Boy development**](https://gbdev.io/guides/tools.html).


### Ohne Code (quasi per Drag & Drop)

- [**GB Studio**](https://www.gbstudio.dev/), der »Drag & Drop Retro Game Creator«
- [**GB Studio Beta Builds**](https://github.com/chrismaltby/gb-studio/tree/v2beta#beta-builds) für Experimentierfreudige


### In C (wie früher)

- [**GBDK-2020**](https://github.com/gbdk-2020/gbdk-2020), The Game Boy Developer’s Kit für die Entwicklung von Spielen für den Nintendo Game Boy (und andere 8-Bit-Konsolen) in C und Assembler
- Die allgemeine Dokumentation zum GBDK: [**GBDK 2020 Docs**](https://bbbbbr.github.io/gbdk-2020/docs/api/index.html)


### In Assembler (wie ganz früher)

- [**RGBDS**](https://github.com/gbdev/rgbds) Toolchain für die Entwicklung von Game Boy-Spiele in Z80-Assembler
- [**RGBDS macOS-Installation**](https://rgbds.gbdev.io/install/macos) via Homebrew
- [**BBEdit Z80-Assembler**](https://derekbolli.wordpress.com/2012/11/16/editing-z80-assembler-zasm-source-files-with-bbedit/) Sprachmodul


## Tutorials und Referenzen für die Entwicklung

- Nintendos offizielle Seite zum [**Game Boy**](https://www.nintendo.de/Unternehmen/Unternehmensgeschichte/Game-Boy/Game-Boy-627031.html)
- Die [**Game Boy Pan Docs**](https://gbdev.io/pandocs/), eine technische Referenz
- [**Awesome Game Boy Development**](https://gbdev.io/list.html) Hard- und Software-Informationen
- GamingMonsters’ [**GameBoy Programming Tutorials**](https://www.youtube.com/playlist?list=PLeEj4c2zF7PaFv5MPYhNAkBGrkx4iPGJo) auf YouTube
- GamingMonsters’ [**Sample Code**](https://github.com/gingemonster/GamingMonstersGameBoySampleCode) auf GitHub
- [**Anmerkungen für Mac-User**](https://gist.github.com/keztricks/863349fd597f8e43f42976a1ca19e263) zu GamingMonsters’ Videos
- [**GB ASM Tutorial**](https://eldred.fr/gb-asm-tutorial/index.html)
- [**Awesome Game Boy Development**](https://github.com/gbdev/awesome-gbdev) kuratierte Liste aller möglichen Entwicklungs-Ressourcen

## Tools, Testen und Debugging

- [**SameBoy**](https://sameboy.github.io/) ist ein Game Boy-Emulator und -Debugger
- [**png2gbtiles**](https://github.com/bbbbbr/gimp-tilemap-gb/tree/master/console) Kommandozeilen-Werkzeug zur Konvertierung von PNGs zu Tilesets und Tilemaps (.gbr, .gbm, .c)
- [**Game Boy Tile Data Generator**](https://github.com/chrisantonellis/gbtdg) (gbtdg), Plattform-unabhängig als Web-App
