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

Leider haben sowohl RetroArch als auch OpenEmu den Nachteil, dass man nicht einfach so, mal eben, ein ROM starten kann, ohne es vorher zu importieren. Weil das aber zumindest bei RetroArch über die Kommandozeile geht, lässt sich das lösen. — Und mittels Automator auf dem Mac kann man es sich noch einfacher machen.

Mein [RetroLaunch-Repository auf GitHub.](https://github.com/marc2o/retrolaunch.git) Enthält das Shell-Script sowie eine Automator-App (die als Droplet z. B. im Dock verwendet kann) und einen Automator-Workflow, der als Schnellaktion im Finder verwendet wird.