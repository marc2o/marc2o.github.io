---
layout: article
language: de-DE
image: /images/kobo-libra-2.jpg
title: Tipps und Tricks für Kobo E-Reader
author: marc2o
tags:
- Kobo
- E-Reader
- eReader
- epub
- Bücher
---

Design und Funktionalität der Kobo E-Reader gefallen mir schon seit gut zehn Jahren. Insbesondere die Vielzahl der lesbaren Dateiformate weiß ich zu schätzen sowie auch die Tatsache, dass sich Bücher von Hand oder mittels Calibre auf das Gerät übertragen lassen, also ohne die pro­p­ri­e­täre Kobo-Software verwenden zu müssen.

Lediglich der Registrierungszwang und der Einsatz der Kobo Desktop-Software für Updates geht mir gegen den Strich. Aber die Kobo-E-Reader haben eine große Community und so gibt es für alles mindestens eine Lösung.

---

Inhalt:

- [Registrierung und Anmeldung umgehen](#registrierung-und-anmeldung-umgehen)
- [Firmware-Updates manuell durchführen](#firmware-updates-manuell-durchführen)
- [Sideloading von Hörbüchern (Audiobooks)](#sideloading-von-hörbüchern-audiobooks)
- [InkBox OS – die alternative Firmware](#inkbox-os-die-alternative-firmware)

---

## Registrierung und Anmeldung umgehen

Bei der Einrichtung eines neuen Kobo E-Readers fragt dieser gleich in einem der ersten Schritte nach dem Kobo-Nutzerkonto. Um das zu umgehen, muss der Weg »ohne Internetverbindung« eingeschlagen werden. Auf dem Display wird die Aufforderung angezeigt, den Reader per USB-Kabel mit dem Computer zu verbinden.

Der Reader wird als Laufwerk angezeigt. In macOS ist er unter dem folgenden Pfad im Terminal erreichbar:

```bash
/Volumes/KOBOeReader/
```

Dort befindet sich der »unsichtbare« `.kobo`-Ordner, in dem die  `KoboReader.sqlite`-Datenbank liegt. Diese enthält unter `user` bislang nur einen Test-Nutzer. Um den Kobo zu »befriedigen« muss hier nun ein neuer Nutzereintrag angelegt werden. Entweder mit SQLite über die Kommandozeile –

```sql
INSERT INTO user(UserID,UserKey) VALUES('1','');
```

– oder beispielsweise mit dem [DB Browser for SQLite](https://sqlitebrowser.org), den es für macOS, Windows und Linux gibt.

Dabei wird in der `user`-Tabelle ein neuer Eintrag angelegt, in dem dann die `userID` mit dem Wert `1` gefüllt wird und der `userKey` leer bleibt.

Wirft man den Reader dann aus und trennt die USB-Verbindung kann die Einrichtung ohne Nutzerkonto und Anmeldung fortgesetzt werden.

## Firmware-Updates manuell durchführen

Kobo Firmware-Updates lassen sich auch ohne die Kobo Desktop-Software durchführen.

### Variante 1: Mit Calibre und Plugins

Wer Calibre als digitale Bibliothek verwendet, kann versuchen, mit den entsprechenden Plugins für Kobo E-Reader die Updates durchzuführen.

- [Kobo Utilities](https://www.mobileread.com/forums/showthread.php?t=215339)-Plugin für Calibre
- [KoboTouchExtended](https://www.mobileread.com/forums/showthread.php?t=211135)-Plugin für Calibre

Für mich hat das leider nicht verlässlich funktioniert. Updates wurden zwar erkannt, konnten jedoch nicht installiert werden.

### Variante 2: Komplett manuell

Auf der Website [Kobo Firmware-Downloads](https://pgaskin.net/KoboStuff/kobofirmware.html) sind alle Firmware-Updates für alle Geräte übersichtlich in einer Tabelle mit zugehörigen Versionsinfos und Download-Links dargestellt.

Der Aktualisierungsvorgang ist denkbar einfach:

1. Firmware für das entsprechende Gerät herunterladen
2. E-Reader per USB-Kabel an den Computer anschließen.
3. Das ZIP-Archiv in den `.kobo`-Ordner des E-Readers entpacken

Sobald der Reader ausgeworfen und das USB-Kabel abgezogen ist, beginnt das Gerät mit der Durchführung der Aktualisierung.

## »Sideloading« von Hörbüchern (Audiobooks)

Leider spielen die Kobo E-Reader nur das Kobo-eigene Dateiformat mit dem nativen Audiobook-Programm ab. Es gibt aber eine Möglichkeit, z. B. bei Thalia erworbene Hörbücher über einen einfachen, integrierten MP3-Player zu hören.

Für diesen alternativen Audioplayer kommen leider weder Ordner mit `.mp3`-Dateien noch das praktische `.m4b`-Format in Frage. Ausschließlich Hörbucher im `.mp3z`-»Format« werden abgespielt. Dabei handelt es sich lediglich um gezippte Ordner mit den durchnumerierten MP3-Dateien.

Für die Verwendung mit dem alternativen Player des Kobo ist es ideal (und fast zwingend nötig), dass das Hörbuch aus möglichst vielen, möglichst kurzen einzelnen Kapiteldateien besteht. Der Player tut sich schwer mit spulen und merkt sich auch keine Abspielposition, sondern lediglich die zuletzt gehörte Datei. Die Hörbücher von thalia.de sind für diese Anwendung sehr gut geeignet.

Liegt ein Hörbuch z. B. als `.m4b`-Datei vor, muss dieses zuerst in Kapiteldateien aufgeteilt werden. Dafür gibt es reihenweise Anwendungen, online wie offline, mit Mausbedienung oder fürs Terminal, mit denen das möglich ist, wie etwa [ocenaudio](https://www.ocenaudio.com), das für macOS, Windows und Linux frei verfügbar ist.

Hat man also einen ordner mit den vielen kurzen Audiodateien, die numerisch benannt sein sollten (z. b. `01.mp3`, `02.mp3` etc.) geht es wie folgt weiter:

1. Ordner mit `.mp3`-Dateien zu einem `.zip`-Archiv komprimieren
2. Alternativ kann bei Büchern von thalia.de direkt das heruntergeladene `.zip`-Archiv verwenden
3. Die Dateiendung in `.mp3z` umbenennen

Da solche Archiv-Hörbücher keine Metadaten haben, empfiehlt es sich, sprechende Namen zu vergeben, z. B.

> `Kafka, Franz - Die Verwandlung.mp3z`

Siehe auch die mobileread-Diskussion [_Sideloading Audiobooks on mobileread_](https://www.mobileread.com/forums/showthread.php?t=342747) und den Artikel [_How to Sideload Audiobooks and MP3s to Kobo eReaders_](https://blog.the-ebook-reader.com/2021/11/10/how-to-sideload-audiobooks-and-mp3s-to-kobo-ereaders/).

## InkBox OS – die alternative Firmware

Nach dem Einzug des Kobo Libra 2 ist jetzt mein Kobo Glo HD arbeitslos. Für die Ausmusterung ist der alte Reader aber eigentlich zu schade. Zu schön ist das größere Display, zu gut liegt der Reader in der Hand. Daher habe ich mich für ein Experiment entschieden: InkBox OS – eine speziell für Kobo E-Reader entwickelte alternative Firmware.

> InkBox OS is an open-source, fully-functional standalone OS for Rakuten Kobo's eReaders. ([inkbox.ddns.net](https://inkbox.ddns.net/))

### InkBox OS 2.0 installieren

Am schwierigsten war es, an die SD-Karte des Readers zu kommen. Dazu muss nämlich die Rückseite vorsichtig gelöst werden. Möglichst, ohne die Plastikwiderhaken abzubrechen. Aber auch das geht

1. mit dem richtigen Werkzeug (siehe auch [iFixIt](https://de.ifixit.com/Anleitung/Kobo+Glo+HD+Rear+Cover+Replacement/135258)-Anleitung),
2. ein bisschen Geduld und Fingerspitzengefühl
3. und wenn man am Schalter oder USB-Anschluss mit der Prozedur beginnt

eigentlich ganz gut.

Nun kann man das [Firmware-Image herunterladen](https://inkbox.ddns.net/downloads.html) und der [Installation-Anleitung](https://inkbox.ddns.net/installation.html) folgen. Die Installation ist allerdings nicht weiter kompliziert, wenn man einfach das Image mit dem  [balenaEtcher](https://etcher.balena.io/) auf die SD-Karte flasht.

SD-Karte wieder einlegen, Gerät einschalten, warten.

<figure>
	<figure><img src="/images/kobo-inkbox-01.jpg" alt=""><figcaption>Startvorgang …</figcaption></figure>
	<figure><img src="/images/kobo-inkbox-02.jpg" alt=""><figcaption>… »Home«-Bildschirm …</figcaption></figure>
	<figure><img src="/images/kobo-inkbox-03.jpg" alt=""><figcaption>… und Reader mit Einstellungen</figcaption></figure>
</figure>
