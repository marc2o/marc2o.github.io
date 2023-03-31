---
layout: article
language: de-DE
image: /images/rp2-lineageos-1.jpg
title: Retroid Pocket 2 LineageOS-Upgrade
author: marc2o
date: 2023-03-25
tags:
- retroid pocket 2
- emulation
- LineageOS
- gaming
- spielkonsole
---

LineageOS 15.1 ist aus der Beta-Phase raus und ich hab mich endlich getraut, die Neueinrichtung meines [Retroid Pocket 2](% link 2021-01-29-Retroid-Pocket-2-Handeheld-Konsole.md %) vorzunehmen.

Das Upgrade lohnt sich für alle, die auf das RetroidOS verzichten können und denen die bisherigen Android 6- und 8.1-Systeme zu schwergängig sind. [LineageOS](https://lineageos.org/) ist ein »free and open-source operating system for various devices, based on the Android mobile platform.« Ohne den ganzen Google-Schnickschnack. Das System fühlt sich insgesamt schlanker und schneller an.

Der Upgrade-Prozess ist recht einfach. Damit nichts schief geht, muss man sich lediglich genau an den mitgelieferten »Retroid Pocket 2 Lineage Guide« (PDF) halten oder das Video von Retro Game Corps »[How to Install LineageOS 15.1 on Retroid Pocket 2](https://www.youtube.com/watch?app=desktop&v=SCJpCgBJDfg)« strikt befolgen.

## Vorbereitung

Benötigt werden:

1. Ausgeschalteter (!) Retroid Pocket 2
2. Ein gutes USB-Kabel, das für Datentransfer geeignet ist
3. Ein Windows-PC (da es leiderkeinen Weg zu geben scheint, den RP2 z. B. am Mac zu flashen)
4. [Google USB Driver](https://developer.android.com/studio/run/win-usb) für die Kommunikation zwischen PC und RP2*
5. [MT65XX Preloader Driver](https://www.ytechb.com/mt65xx-preloader-driver/) für die Verwendung von SPFlash
6. [Lineage-Firmware](https://drive.google.com/drive/folders/1glkep6Jb4h27dsOFEtlsOHycMUS2E4kG) mit LineageOS und SPFlash
7. [MindTheGapps (Play Store)](https://androidfilehost.com/?fid=3700668719832236373)
8. Die [Stock Apps](https://drive.google.com/drive/folders/1b75bVzYlNlPv3jSSf3s7A0k8zsFGwk7R), d. h. die zum RP2 gehörigen Application Packages

Die Links zu den Treibern, der Firmware und den Apps befinden sich auf der [Firmware-Seite](https://wiki.retroidhandhelds.com/index.php?title=Firmware) der Retroid Handhelds-Wiki sowie im PDF-Leitfaden.

Die Stock Apps habe ich direkt in ein Verzeichnis auf der SD-Karte kopiert.

## Flash-Prozess

1. USB- und MT65XX-Treiber installieren
2. PC neustarten
3. SPFlash starten (zu finden unter ´Lineage-15.1-RP2/SPFlash`) und entsprechend konfigurieren:
	
	* Download-Agent: `MTK_AllInOne_­DA.bin`
	* Scatter-loading File: `MT6580_Android_scatter.txt`

4. Die Option `Format All + Download` auswählen
5. Dann `Download`-Button anklicken
6. **Erst jetzt (!)** den **ausgeschalteten (!)** Retroid Pocket 2 per USB an den PC anschließen
7. Auf die `Download OK!`-Dialogbox warten
8. Den RP2 abstöpseln und einschalten; er bootet nun in den Recovery-Mode

## LineageOS installieren

Im Recovery-Mode funktionieren weder Gamepad-Buttons noch Sticks. Das Navigieren durch die Menü-Elemente erfolgt mittels `laut/leise`, die Auswahl eines Elements durch einen kurzen Druck auf den den `ein/aus`-Knopf.

1. Als erstes die Option `Factory reset`auswählen, bestätigen und danach `Wipe data / factory reset` bestätigen.
2. Nun `Apply update` auswählen und im nächsten Schritt die Option `Apply from ADB` bestätigen.
3. Jetzt die `Lineage Installer.bat` starten. Ein Konsolen-Fenster öffnet sich. Das Script scheint bei 47 % stehen zu bleiben. Aber am RP2 läuft alles weiter. Das Fenster verschwindet von selbst, sowie der Prozess am RP2 beendet ist.
4. Nun das gleich noch mal, um den Playstore zu installieren, also `Apply update`, dann `Apply from ADB` …
5. Jetzt die `Play Store Installer.bat` ausführen. Wieder öffnet sich ein Konsolen-Fenster, wieder scheint das Script bei 47 % hängen zu bleiben, und wieder schließt sich das Fenster von selbst, wenn am RP2 alles erledigt ist.
6. Das war’s. Nun `Reboot` wählen und den RP2 machen lassen.

## Einrichtung

Nach dem Neustart wird LineageOS eingerichtet. Der Setup-Assistent führt durch die Schritte. Hier kann man auch RePoLa als Menü auswählen.

<figure>
	<img src="/images/rp2-lineageos-2.jpg" alt="Retroid Pocket 2 Konsole mit LineageOS 15.1"><figcaption>Retroid Pocket 2 mit LineageOS 15.1. RePoLa ist direkt vorinstalliert.</figcaption>
</figure>

Nun können die Stock Apps, von der SD-Karte aus installiert werden. Ich würde empfehlen, zuerst den `MiXplorer` zu installieren und dann mit diesem fortzufahren.

## ROMs mit einem Mac an den RP2 übertragen

Für Mac-Nutzer neuerer Geräte mit Apple Chips stehen zwei Möglichkeiten zur Verfügung, um Dateien an den Retroid Pocket 2 zu übertragen.

**1. Direkt die SD-Karte verwenden,** also die SD-Karte aus dem RP2 entfernen und (mittels Card Reader) in den Mac einstecken. Da macOS für jede kopierte Datei eine unsichtbare Datei erzeugt, entferne ich diese vor dem Auswerfen der SD-Karte wie folgt:

```bash
cd /pfad/zur/SD-Karte
find . -name '.\_\*' -exec rm -rf {} \\; -print
```

**2. Mit OpenMTP,** einer Android-File-Transfer-App für macOS: https://openmtp.ganeshrvel.com/. Diese funktioniert erstaunlich gut.
