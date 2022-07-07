---
layout: article
language: de-DE
image: /images/pocketchip.jpg
title: Die Reanimation meines PocketCHIP
author: marc2o
tages:
- PocketCHIP
- Retro
- Computer
- Linux
- macOS
- Synthesizer
- Spielkonsole
- Terminal
---

Am [PocketCHIP](http://chip.jfpossibilities.com/docs/pocketchip.html) bin ich damals in 2017 nicht vorbei gekommen (das war noch vor meinem [ODROID GO](2019-04-17-ODROID-GO-Der-Spielspass-Bausatz.md) und [Retroid Pocket 2](2021-01-29-Retroid-Pocket-2-Handeheld-Konsole.md)): ein kleiner vollwertiger Computer mit Tastatur und Bildschirm, auf dem spannende Entwicklungs- und Musik-Programme vorinstalliert waren. Das Ganze ist also eine Spielkonsole, ein Computer, ein tragbarer Synthesizer — und eben ein kleiner Linux-Computer.

Leider ist der Hersteller NextThing Co. recht fix pleite gegangen. Support und Update-Server waren schon bald darauf nicht mehr erreichbar. Glücklicherweise haben Fans die Repositories geklont und Tipps veröffentlicht, wie die geräte aktualisiert werden können.

Wenn man einen Mac hat, ist das allerdings nicht ganz so einfach, den CHIP zu flashen. Schon mein letzter Versuch war diesbezüglich eine Herausforderung. Da ich keinen Windows-Rechner hab und eine Emulation bzw. VM nicht funktioniert, habe ich es diesmal anders probiert: Ich hab mir eine bootfähige SD-Karte mit Ubuntu eingerichtet und meinen Mac von dieser gestartet.


## Ubuntu auf einer SD-Karte

Ich hatte noch eine schnelle SanDisk 8-GB-Karte, die für diesen Zweck ideal ist. Als System habe ich mir Ubuntu Desktop ausgesucht.

1. Disk-Image herunterladen (`.iso`-Datei): [22.04 LTS](https://ubuntu.com/download/desktop)
2. Den [balenaEtcher](https://www.balena.io/etcher/) für macOS herunterladen und das Image auf einen simplen USB-Stick »flashen« (4 GB reichen völlig)
3. Den Mac von diesem Stick booten 

Ist Ubuntu fertig geladen (beim Startvorgang ausprobieren wählen, nicht installieren), kann das Terminal gestartet werden. Nun folgt nämlich die Einrichtung der SD-Karte, wofür erstmal `mkusb` installiert werden muss.

```bash
sudo add-apt-repository universe
sudo add-apt-repository ppa:mkusb/unstable
sudo apt update
sudo apt install mkusb
# optional...
sudo apt install usb-pack-efi
```

Im Anschluss `mkusb` ausführen und die SD-Karte mit Ubuntu als »Live-System mit persistentem Speicher« einrichten.

1. Die »Classic«-Option mit einfacher Bedienung wählen
2. Option `i Install (make a boot device)` wählen
3. Option `p Persistent Live – only Debian and Ubuntu` wählen
4. Als Quelle das Ubuntu-Image auswählen
5. Als Ziel die SD-Karte auswählen
6. Falls die Frage kommt, `upefi usb-pack-efi (default grub from ISO file)` wählen
7. Dann das `Go` geben

Das ist alles. Nun kann man von der SD-Karte booten.


## PocketCHIP flashen

Der folgende Leitfaden beruht auf dem Guide von [luzhuomi](https://gist.github.com/luzhuomi/526fbcc30f3522f09eacf20d0f776fa5) und ist um eigene Erkenntnisse aus den Fehlermeldungen ergänzt.

Den CHIP aus dem Gehäuse des PocketCHIP herauslösen. Mit einer Büroklammer `FEL` mit einem `GND` verbinden.

Mittels Terminal in einem beliebigen Ordner das [Flash-CHIP](https://github.com/Thore-Krug/Flash-CHIP)-Script installieren.

```bash
sudo add-apt-repository universal 
sudo apt update
# ggf. git installieren, falls nicht vorhanden
git clone https://github.com/thore-krug/Flash-CHIP.git
```

Nun mit `cd` in das `Flash-CHIP` wechseln und mit `sudo chmod +x Flash.sh` das Script ausführbar machen.

Schließlich das Script ausführen: `./Flash.sh`.


### Ungültiger Parameter `-i`?

In neueren Versionen von `fastboot` werden die Optionen `-i` und `-u` nicht mehr benötigt. Daher wird eine Fehlermeldung angezeigt — und die gleich zig mal.

Damit das Script fehlerfrei läuft müssen einfach nur alle Dateien angepasst, d. h. die entsprechenden Optionen entfernt werden So etwas beispielsweise 

```bash
fastboot -i 0x1f3a -u flash UBI ${SPARSE_UBI}
```

muss wie folgt geändert werden

```bash
fastboot flash UBI ${SPARSE_UBI}
```

— das ist alles.

Mit `grep -r fastboot *`kann man sich alle Dateien anzeigen lassen, die geändert werden müssen.

Dann noch mal das Flash-Script ausführen.

Wenn alles glatt geht, ist der CHIP fertig geflasht und kann wieder in das Gehäuse eingesetzt werden.


## Debian »Jessie« aktualisieren

Jetzt kann man den CHIP wieder einsetzen und den PocketCHIP booten.

Zunächst muss dann die `sources.list` angepasst werden, da diese noch Verweise auf die alten Server enthält, die längst offline sind.

```bash
sudo nano /etc/apt/sources.list
```

So müssen die Zeilen nach der Bearbeitung aussehen.

```bash
deb http://ftp.us.debian.org/debian/ jessie main contrib non-free
deb-src http://ftp.us.debian.org/debian/ jessie main contrib non-free
    
deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free
    
deb http://chip.jfpossibilities.com/chip/debian/repo jessie main
deb http://chip.jfpossibilities.com/chip/debian/pocketchip jessie main
```

Die Aktualisierung starten.

```bash
sudo apt install debian-keyring debian-archive-keyring
sudo apt update && sudo apt upgrade
```

## Wenn alles gut gegangen ist…

<figure>
    <figure><img src="/images/pocketchip-install.jpg" alt=""><figcaption>Update und Upgrade</figcaption></figure>
    <figure><img src="/images/pocketchip-splash.jpg" alt=""><figcaption>So sieht es aus, wenn alles geklappt hat.</figcaption></figure>
    <figure><img src="/images/pocketchip-phase.jpg" alt=""><figcaption>Phase Synthesizer</figcaption></figure>
    <figure><img src="/images/pocketchip-sunvox.jpg" alt=""><figcaption>SunVox Music Studio</figcaption></figure>
</figure>


## Feinschliff

Auf GitHub gibt es eine schöne Checkliste von [boogah](https://gist.github.com/boogah/ac6f6f082b91fa976ae8bd45e5120d4a) mit Dingen, die man beim PocketCHIP »als erstes« machen sollte.

```bash
# Passwort ändern
passwd
# Root User
$ sudo -i
# Updates
apt-get update && apt-get upgrade && apt-get dist-upgrade
# Lokale Zeitzone einrichten
apt-get install locales
dpkg-reconfigure tzdata
locale-gen en_US en_US.UTF-8
# OpenSSH
apt-get install openssh-server
iw wlan0 set power_save off
# Backup
apt-get install rsync
# Git
apt-get install git-all
```


### SSH-Verbindung vom Mac aus aufnehmen

Falls SSH auf dem PocketCHIP noch nicht läuft, den Service starten. 

```bash
sudo service ssh start
# IP-Adresse des PocketCHIP angeigen
ip addr show wlan0
```

Vom Mac aus meldet man sich dann so auf dem PocketCHIP an:

```bash
ssh chip@192.168.178.36
# Das Standard-Passwort lautet chip, falls es nicht geändert wurde
```

Um Daten vom Mac an den PocketCHIP zu senden, benutzt man `scp`.

```bash
scp /pfad/zur/lokalen/datei chip@192.168.178.36:/pfad/zum/ziel/
```


### Das HOME-Menü anpassen

Man kann die Konfiguration des HOME-Menüs anpassen und eigene Programme einbinden: `sudo nano /usr/share/pocket-home/config.json`. Icons liegen z. B. in `/usr/share/pocket-home/appIcons` bzw. können dort angelegt werden.


## Spannende Software für den PocketCHIP

### Phase Distortion Synthesizer

Die aktuelle Version gibt es hier: http://www.humbletune.com/phase/.

Die Installation kann einfach über das Terminal erfolgen.

```bash
mkdir $HOME/phase
cd $HOME/phase

curl --remote-name http://www.humbletune.com/phase/chip/phase.zip
unzip phase.zip
```

Danach die `.asoundrc`-Datei bearbeiten.

```bash
pcm.!default {
	type plug
	slave.pcm "dmixer"
}
pcm.dsp0 {
	type plug
	slave.pcm "dmixer"
}
pcm.dmixer {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 1024
		buffer_size 8192
		rate 22050
	}
	bindings {
		0 0
		1 1
	}
}
ctl.mixer0 {
	type hw
	card 0
}
pcm.phase {
	type plug
	slave.pcm "dmixer"
}
```

Alternativ können alle Settings auch direkt heruntergeladen werden.

```bash
curl --remote-name http://www.humbletune.com/phase/chip/.asoundrc
curl --remote-name http://www.humbletune.com/phase/chip/settings.json
```

Dann den PocketCHIP neu starten.


### PICO-8 Fantasy Console

Zwar ist PICO-8 vorinstalliert, aber nach dem Update des Systems wollte die Fantasy Console nicht mehr starten. Hier gibt es die neue Version: https://www.lexaloffle.com/bbs/?tid=34009.

Diese kann entweder als ZIP-Archiv heruntergeladen oder direkt auf dem PocketCHIP installiert werden.

```bash
wget www.lexaloffle.com/dl/chip/pico-8\_0.2.4c\_chip.zip
sudo unzip pico-8\_0.2.4c\_chip.zip -d /usr/lib
```


### SunVox Modular Music Studio

Dieses modulare Music-Studio gibt es für fast alle Plattformen. Dazu einfach die aktuelle Version hier herunterladen: https://warmplace.ru/soft/sunvox/.

Im Ordner `sunvox/linux_arm_armel_maemo/` befindet sich die Debian-Version für ARMv7. Diese dann beispielweise via SSH an den PocketCHIP übertragen.

MIDI-In funktioniert übrigens auch. Ich habe mein AKAI Professional MPK mini Play MK3 an den USB-Port des PocketCHIP angeschlossen und dann SunVox gestartet. Sogar die Stromversorgung über USB reicht für das Gerät aus. Die signale kommen zwar leicht verzögert an, aber für eine Schrittweise Noteneingabe geht das.

Mit `amidi -l` kann man sich im Terminal übrigens die verfügbaren MIDI-Geräte auflisten lassen.

<!--
## Auf Debian bis Version 11 »Bullseye« upgraden

In der `sources.list` die beiden `chip`-Verweise auskommentieren:

```bash
deb http://ftp.us.debian.org/debian/ jessie main contrib non-free
deb-src http://ftp.us.debian.org/debian/ jessie main contrib non-free
    
deb http://security.debian.org/ jessie/updates main contrib non-free
deb-src http://security.debian.org/ jessie/updates main contrib non-free
    
# deb http://chip.jfpossibilities.com/chip/debian/repo jessie main
# deb http://chip.jfpossibilities.com/chip/debian/pocketchip jessie main
```

Dann Jessie durch Stretch ersetzen:

```bash
sudo sed -i s/jessie/stretch/ /etc/apt/sources.list
```

Schließlich die Updates und Upgrades ausführen:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

XXX

## Von Jessie zu Stretch

Um von Jessie zu Stretch upzugraden wieder die `sources.list` anpassen. Dazu die folgenden beiden Zeilen auskommentieren:

```bash
# deb http://chip.jfpossibilities.com/chip/debian/repo jessie main
# deb http://chip.jfpossibilities.com/chip/debian/pocketchip jessie main
```

Die anderen Zeilen müssen dann wie folgt aussehen:

```bash
deb http://ftp.us.debian.org/debian/ stretch main contrib non-free
deb-src http://ftp.us.debian.org/debian/ stretch main contrib non-free
    
deb http://security.debian.org/ stretch/updates main contrib non-free
deb-src http://security.debian.org/ stretch/updates main contrib non-free
```

Dann `sudo apt update && sudo apt full-upgrade` ausführen.

Die Datei `/etc/NetworkManager/NetworkManager.conf` wie folgt anpassen:

```bash
[main]
plugins=ifupdown,keyfile

[connection]
wifi.mac-address-randomization=1

[device]
wifi.scan-rand-mac-address=no

[ifupdown]
managed=false

[keyfile]
unmanaged-devices=interface-name:wlan1
```

Falls X verwendet wird, die `/etc/X11/xorg.conf` folgendermaßen anpassen:

```bash
Section "Files"
    ModulePath "/usr/lib/arm-linux-gnueabihf/xorg/modules/"
    ModulePath "/usr/lib/xorg/modules/"
EndSection

Section "Monitor"
    Identifier	"VGA"
    Option		"PreferredMode"	"1024x768_60.00"
EndSection

Section "Monitor"
    Identifier	"HDMI"
    Option		"PreferredMode"	"1280x720_60.00"
EndSection

Section "Monitor"
    Identifier	"Composite"
    Option		"PreferredMode"	"NTSC10"
EndSection

Section "Device"
    Identifier	"Allwinner sun4i DRM"
    Driver		"armsoc"
    Option		"Monitor-Composite-0"	"Composite"
    Option		"Monitor-VGA-0"		"VGA"
    Option		"Monitor-HDMI-A-0"	"HDMI"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device		"Card0"
EndSection


Section "Device"
    Identifier	"Card0"
    Driver		"modesetting"
EndSection
```

Den PocketCHIP neustarten.


## Von Stretch zu Buster

Die `/etc/apt/source.list` erneut anpassen:

```bash
deb http://deb.debian.org/debian/ buster main contrib non-free
#deb-src http://deb.debian.org/debian/ buster main contrib non-free
#deb http://security.debian.org/ buster/updates main contrib non-free
#deb-src http://security.debian.org/ buster/updates main contrib non-free
#deb http://deb.debian.org/debian buster-backports main contrib non-free
#deb-src http://deb.debian.org/debian buster-backports main contrib non-free
```

Danach `sudo apt update && sudo apt full-upgrade` ausführen.

Und wieder `/etc/X11/xorg.conf` bearbeiten:

```bash
Section "Files"
    ModulePath "/usr/lib/arm-linux-gnueabihf/xorg/modules/"
    ModulePath "/usr/lib/xorg/modules/"
EndSection

Section "Monitor"
    Identifier	"VGA"
    Option		"PreferredMode"	"1024x768_60.00"
EndSection

Section "Monitor"
    Identifier	"HDMI"
    Option		"PreferredMode"	"1280x720_60.00"
EndSection

Section "Monitor"
    Identifier	"Composite"
    Option		"PreferredMode"	"NTSC10"
EndSection


Section "Screen"
    Identifier	"Screen0"
    Device		"Card0"
EndSection


Section "Device"
    Identifier	"Card0"
    Driver		"fbdev"
EndSection
```

Optional können `lightdm` und `i3` installiert werden (siehe diese [Anleitung von u/Hexada auf Reddit](https://www.reddit.com/r/ChipCommunity/comments/abndo9/an_updated_guide_for_installing_i3_window_manager/)).

Den PocketCHIP neustarten.


### Cursor-Bewegungen invertiert?

Falls die Touch-Screen-Cursor-Bewegungen invertiert sind, müssen die folgenden zeilen entweder an die `/etc/X11/xorg.conf` oder `/usr/share/X11/xorg.conf.d/99-calibration.conf` angehängt werden:

```bash
Section "InputClass"
    Identifier "calibration"
    MatchProduct "1c25000.rtp"
    Option "Calibration"  "3992 182 3694 276"
    Option "SwapAxes" "0"
    Option "TransformationMatrix" "-1 0 1 0 -1 1 0 0 1"
EndSection
```

### Wenn Drücken des HOME-Knopfes den PocketCHIP ausschaltet…

Die folgende Zeile in der `/etc/systemd/logind.conf` ändern:

```bash
#HandlePowerKey=poweroff
HandlePowerKey=ignore
```

Dann `systemctl kill -s HUP systemd-logind`.


http://stevemcgrath.io/post/2016-07-16-setting-up-pocketchip/

-->