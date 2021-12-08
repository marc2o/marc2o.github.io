---
layout: article
language: de-DE
image: /images/...
title: Ein minimalistischer Launcher für RetroArch
author: marc2o
tags:
- retro gaming
- emulation
- retroarch
- development
- bash
- mac
- automator
---

Wer gern Retro-Spiele spielt, hat entweder für jede Konsole einen Emulator oder eben einen Multi-Emulator für alle Konsolen. Auf dem Mac ist sicherlich [OpenEmu](https://openemu.org) der schönste »Emu«. Aber durch meinen [Retroid Pocket 2]({% post_url 2021-01-29-Retroid-Pocket-2-Handeheld-Konsole %}) hab ich mich aber sehr an [RetroArch](https://www.retroarch.com/) gewöhnt.

Leider haben sowohl RetroArch als auch OpenEmu den Nachteil, dass man nicht einfach so, mal eben, ein ROM starten kann, ohne es vorher zu importieren. Weil das aber zumindest bei RetroArch über die Kommandozeile geht, lässt sich das lösen. — Und mittels Terminal und Automator auf dem Mac kann man es sich noch einfacher machen.

Zuerst der Pfad zu den Emulations-Kernen für RetroArch. Die liegen tief im Nutzerordner verborgen. Dann die Namen der Kerne selbst.

Für beides habe ich einfach ein paar Konstanten definiert.

```bash
cpath=$HOME/Library/Application\ Support/RetroArch/cores/

nes=fceumm_libretro.dylib
gbc=gambatte_libretro.dylib
gba=mgba_libretro.dylib
snes=snes9x_libretro.dylib
a26=stella_libretro.dylib
smd=genesis_plus_gx_libretro.dylib
nds=desmume_libretro.dylib
c64=vice_x64_libretro.dylib
```

Der clevere Teil passiert dann in der Hauptschleife. Bei Automator ist es notwendig, auf »Parameter« umzuschalten, damit die übergebenen ROMs nicht and `stdin` übergeben werden. In der Schleife werden der Name des ROMs sowie die Datei-Endung ausgeschnitten. Danach folgt der Abgleich 

```bash
for rom in "$@"
do
	romname=$(basename -- "$rom")
	romtype="${romname#*.}"

  # choose core based on rom suffix
	case "$romtype" in
		nes)            core=$nes ;;
		gb|gbc)         core=$gbc ;;
		smc|sfc)        core=$snes ;;
		a26|bin)        core=$a26 ;;
		sms|md|smd|gg)  core=$smd ;;
		nds)            core=$nds ;;
		d64|t64|prg)    core=$c64 ;;
	esac

done
```

Mein [RetroLaunch-Repository auf GitHub.](https://github.com/marc2o/retrolaunch.git) Enthält das Shell-Script sowie eine Automator-App (die als Droplet z. B. im Dock verwendet kann) und einen Automator-Workflow, der als Schnellaktion im Finder verwendet wird.