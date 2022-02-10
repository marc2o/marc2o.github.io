---
layout: article
language: de-DE
image: /images/...
title: Spiele entwickeln das Nintendo Entertainment System (Famicom)
author: marc2o
tags:
- spiele
- entwicklung
- game development
- nintendo entertainment set
- famicom
- mac
---

Mit den Spielen, die man heute so »retro« nennt, bin ich aufgewachsen. Daher habe ich zu alten Computern und Konsolen ein besonderes Verhältnis. Ich mag die besonderen Einschränkungen der alten Systeme und die Kreativität, die es erfordert, trotz dieser Einschränkungen etwas zu bewerkstelligen, das functioniert, Spaß macht und gut aussieht.

Dass ich damit nicht allein bin zeigt die Aktivität der Homebrew-Szene — und gerade die Neuentwicklungen für das NES faszinieren mich. Beispielsweise sind [Micro Mages](http://morphcat.de/micromages/), [Nebs ’n Debs](https://www.nebsndebs.com/) und [Witch n' Wiz](https://mhughson.itch.io/witch-n-wiz) hervorragende Spiele mit super Musik und Grafik. [Alter Ego](https://www.retrosouls.net/?page_id=614) ist eines meiner absoluten Lieblingsspiele.

Weil ich das zu gern mal selbst ausprobieren möchte, habe ich hier eine Übersicht it Tipps und Links zusammengestellt (eher für mich, als persönliche Link-Sammlung).


## Welche Werkzeuge und Dokumentationen gibt es?

Als erstes gilt es, die richtigen Werkzeuge für die Entwicklung zu wählen. Das ist wichtig, denn davon hängt ab, wie viel Arbeit das geplante Spiel machen wird, was möglich sein wird und wie schnell das Spiel läuft. Für das NES bietet sich Assembler an. Das Herz des NES ist der Ricoh 2A03, ein MOS 6502-Derivat — und der 6502 ist ein super dokumentierter Prozessor, der in einer ganzen Reihe von 8-Bit-Computern und -Konsolen seinen Dienst getan hat: vom Atari 2600 über den Apple II bis hin zum Commodore C64 und eben im Nintendo Entertainment System / Famicom. 6502-Assembler ist eine recht übersichtliche Sprache und es stehen verschiedene Assembler, je nach Geschmack, zur Verfügung.


### Programmierung (in 6502-Assembler und eventuell C)

* [NESASM3](https://github.com/camsaul/nesasm): Wohl der Ur-Assembler für die NES-Entwicklung
* [ASM6f](https://github.com/freem/asm6f): ein auf NESdev beliebter Assembler
* [CA65](https://github.com/cc65/cc65): Assembler, C-Compiler und Linker für 6502-Systeme


### Tipps, Anleitungen und Beispiele

- [NROM-, UNROM- und CNROM-Templates](https://forums.nesdev.org/viewtopic.php?t=6160) für ASM6
- [NROM-Template](https://github.com/pinobatch/nrom-template) für CA65
- [NES-Hilfsprogramme](https://github.com/qalle2/nes-util)
- [PNG2CHR](https://github.com/Taywee/png2chr) (& CHR2PNG) Python-Skripte zur Konvertierung zwischen PNG und NES-CHR-Dateien
- [CHRxPNG](https://) ist mein eigenes Tool, um aus PNGs CHRs zu machen und umgekehrt
- [NES Lightbox](https://famicom.party/neslightbox/)
- [CA65-Guide](https://www.cc65.org/doc/ca65.html)
- [NESdev-Wiki](https://wiki.nesdev.org/w/index.php?title=Nesdev_Wiki)
- [NESdev-Foren](https://forums.nesdev.org/viewforum.php?f=24&sid=a9934fbaae1b2d65890083f38ac5db6b)
- [NESdev-Discord](https://discord.gg/pTWwBCp)
- [Nerdy Nights](https://github.com/ddribin/nerdy-nights)


## Mein Werkzeugkasten (oder neudeutsch: Toolchain)

### Code

Ich programmiere in 6502-Assembler und verwende dazu das **CC65**-Paket. Es ist beliebt und daher verbreitet. Auf macOS einfach über Homebrew installieren:

```bash
brew install cc65
```

In den meisten Fällen kann man sein Programm in nur einer Zeile assemblieren und linken:

```bash
cl65 -t nes -o mygame.nes mygame.s
```

Dieses Beispiel setzt voraus, das die cc65-eigene [`nes.cfg`](https://github.com/cc65/cc65/blob/master/cfg/nes.cfg) verwendet wird.

Ansonsten kann man auch eigene Konfigurationen verwenden und getrennt assemblieren und linken. Dies kann sinnvoll sein, wenn man auch debuggen möchte.

```bash
# assemblieren...
ca65 mygame.s -g -o mygame.o
# linken...
ld65 -o mygame.nes -C mygame.cfg mygame.o -m mygame.map.txt -Ln mygame.labels.txt --dbgfile mygame.nes.dbg
# fertig.
```


### Grafik

Meine Sprites und Tiles pixele ich mit [**GrafX2**](https://pulkomandy.tk/projects/GrafX2/downloads). Das Programm ist stark von Deluxe Paint beeinflusst und daher perfekt für Nostalgiker. Außerdem arbeitet es mit indizierten Farben.

Um aus den 16-Bit-PNGs 2-Bit-PNGs zu machen, verwende ich [**ImageMagick**](https://imagemagick.org) `convert`. Ebenfalls über Homebrew installieren:

```bash
brew install imagemagick
```

Bilder konvertieren:

```bash
convert -depth path/to/input.png path/to/output.png
```


Aus diesen 2-Bit-PNGs werden dann mittels [**png2chr**](https://github.com/Taywee/png2chr) die für das NES nötigen CHR-Dateien. Dazu die Dateien von Github herunterladen und installieren:

```bash
# PNG-Modul
pip3 install pypng
# png2chr und chr2png
python3 path/to/setup.py install
```

Mit `png2chr` lassen 2-Bit-PNG-Dateien in CHR-Dateien umwandeln; mit `chr2png` umgekehrt. Die Syntax ist gleich.

```bash
png2chr -i path/to/tiles.png -o path/to/tiles.chr
```

Da macOS nur mit einer älteren Python-Version ausgestattet ist, muss Python 3 installiert werden, z. B. über Homebrew: `brew install python`. Die neue Version ist über `python3`und `pip3`verfügbar.


### Musik

Die Musik mache ich mit MML und verwende dafür, ganz stilecht, [**PPMCK**](https://github.com/munshkr/ppmck). Runterladen, mittels `make` erstellen und bei Bedarf erstellen. Um mir die Installation zu ersparen, habe ich das `mknsf`-Skript angepasst:

```bash
#!/bin/sh
# PPMCK setup
export PPMCK_BASEDIR=$HOME/Dropbox/Development/ppmck
export PATH=$PATH:$PPMCK_BASEDIR/bin
export NES_INCLUDE=$PPMCK_BASEDIR/nes_include

if [ $# -lt 1 ]; then
  echo "Usage: mknsf MML_FILE"
  exit 1
fi

mml_file=$1

# Compile MML
rm -f effect.h
ppmckc_e -i $mml_file
ppstatus=$?
if [ ! -e effect.h ]; then
  exit $ppstatus
fi

# Assemble
rm -f ppmck.nes
nesasm -s -raw ppmck.asm
ppstatus=$?
if [ ! -e ppmck.nes ]; then
  exit $ppstatus
fi

# Extract name from filename
mml_name=$(basename "$mml_file")
mml_name="${mml_name%.*}"
mv -f ppmck.nes ${mml_name}.nsf
echo "${mml_name}.nsf written"

# Clean temp files
rm -f ${mml_name}.h effect.h define.inc
```

Eine NSF-Datei wird dann wie folgt erstellt:

```bash
mknsf path/to/song.mml
```

Statt MML ist auch das [**FamiStudio**](https://famistudio.org/) eine spannende Option. Das hat sogar eine eigene NES-Sound-Engine.

