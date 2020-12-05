---
layout: article
title: ODROID-GO, der Spielspaß-Bausatz
author: marc2o
language: de-DE
image: /images/odroid-go-customized.jpg
---

# ODROID-GO: Der Spielspaß-Bausatz

Als ich das erste Foto des [ODROID-GO](https://www.hardkernel.com/shop/odroid-go/) gesehen hatte, wusste ich, dass ich einen haben muss! — Schon an NextThing’s [Pocket C.H.I.P.](https://shop.pocketchip.co/collections/frontpage/products/pocket-c-h-i-p-new) mit [PICO-8](https://www.lexaloffle.com/pico-8.php) mit bin ich nicht vorbeigekommen. Da konnte ich bei einem »Gameboy«-Bausatz mit 8-Bit-Emulatoren erst recht nicht widerstehen.

<figure>
<img src="/images/odroid-go-assembled.jpg" alt="Fertiger ODROID-GO">
<figcaption><em>Mein liebstes Spielzeug … nach meinem 3DS (<a href="https://www.instagram.com/p/BndqGnWn6QS/">@marc2o</a>)</em></figcaption>
</figure>

Der ODROID-GO lässt sich leicht zusammenbauen. Kein Löten, nur Schrauben und Stecken. Einfach die beigelegte Anleitung befolgen. Das kann auch jemand, der bis jetzt nur LEGOs zusammengesteckt hat.

Auch das anschließende *customizen* war relativ einfach. Ich wollte, nachdem ich schon einige Fotos gesehen hatte, dass er noch mehr wie ein echter Gameboy aussieht. Also Farbe im Baumarkt gekauft (Dupli-Color RAL 9001) und dann gemäß dieser Anleitung bearbeitet: [Custom Paint-Job für den ODROID-GO](https://ameridroid.com/blogs/ameriblogs/how-to-add-some-color-to-your-odroid-go). 

Die Buttons gibt es bei [Retro Modding](https://www.retromodding.com/collections/gameboy-pocket/products/gameboy-pocket-buttons). Es müssen die vom Gameboy Pocket sein; die normalen sind zu groß. Ich musste allerdings trotzdem noch ein bisschen feilen, damit die Knöpfe leichtgängiger werden und besser rutschen. Das Steuerkreuz passte hingegen gleich wie angegossen.

<figure class="gallery">
	<figure><img src="/images/odroid-go-assembly-1.jpg" alt=""><figcaption><em>Viele Einzelteile</em></figcaption></figure>
	<figure><img src="/images/odroid-go-assembly-2.jpg" alt=""><figcaption><em>Die alternativen Buttons zurecht fummeln, damit sie in die Aussparungen passen</em></figcaption></figure>
	<figure><img src="/images/odroid-go-assembly-3.jpg" alt=""><figcaption><em>Probehalber zusammenschrauben</em></figcaption></figure>
	<figure><img src="/images/odroid-go-assembly-4.jpg" alt=""><figcaption><em>Dann alles schön abkleben…</em></figcaption></figure>
	<figure><img src="/images/odroid-go-assembly-6.jpg" alt=""><figcaption><em>…, im GameBoy-Look einsprühen und trocknen lassen.</em></figcaption></figure>
</figure>

Zu guter letzt habe ich mir noch den [Headphone Audio Hat + DAC](https://backofficeshow.com/shop/odroidgohat) gegönnt, damit ich die Chiptunes mehr genießen kann. — Gerade hab ich gesehen, dass es im Thingyverse dafür ein [Cover](https://www.thingiverse.com/thing:3110057) gibt. Leider hab ich keinen 3D-Drucker.

Hier sammle ich ab jetzt Infos zum ODROID-GO, damit ich alles an einer Stelle habe.


## Tastaturkürzel

<figure>
	<table>
	    <tr>
	        <th>Anwendung</th>
	        <th>Tastenkürzel</th>
	        <th>Funktion</th>
	    </tr>
	    <tr>
	        <td>System</td>
	        <td>[B] beim Einschalten gedrückt halten</td>
	        <td>Startet ODroid Go im Firmware-Update-Modus</td>
	    </tr>
	    <tr>
	        <td>Go-Play</td>
	        <td>[Start] beim Einschalten gedrückt halten</td>
	        <td>Spiel zurücksetzen</td>
	    </tr>
	    <tr>
	        <td>Go-Play</td>
	        <td>[Menue] beim Einschalten gedrückt halten</td>
	        <td>Emulator zurücksetzen</td>
	    </tr>
	    <tr>
	        <td>Go-Play</td>
	        <td>[Start] + [Rechts]</td>
	        <td>Darstellungsmodus: Pixel Perfect oder Skaliert</td>
	    </tr>
	    <tr>
	        <td>Go-Play</td>
	        <td>[Start] + [Hoch]/[Runter]</td>
	        <td>Bildschirmhelligkeit</td>
	    </tr>
	    <tr>
	        <td>Go-Play</td>
	        <td>[Volume] + [Rechts]</td>
	        <td>Audioausgabe: Lautsprecher oder Kopfhörer (mit ODroid GO Audio DAC von The Backoffice)</td>
	    </tr>
	    <tr>
	        <td>Pokémon Crystal</td>
	        <td>[Select] + [Runter] + [B] im Startbildschirm drücken</td>
	        <td>Uhrzeit einstellen </td>
	    </tr>
	    <tr>
	        <td>c64-go</td>
	        <td>[Select]</td>
	        <td>Funktionsmenü anzeigen, z. B. um Tastatur einzublenden</td>
	    </tr>
	    <tr>
	        <td>c64-go</td>
	        <td>[Start]</td>
	        <td>Run/Stop-Taste</td>
	    </tr>
	    <tr>
	        <td>c64-go</td>
	        <td>[B]</td>
	        <td>Space (Leertaste)</td>
	    </tr>
	    <tr>
	        <td>Super Go Play</td>
	        <td>[Select] + [Left]/[Right]</td>
	        <td>Gameboy Farbpaletten wechseln</td>
	    </tr>
	    <tr>
	        <td>Super Go Play</td>
	        <td>[Volume] + [Up]/[Down]</td>
	        <td>Lautstärke einstellen</td>
	    </tr>
	</table>
</figure>

## Firmware-Update auf Mac durchführen

Die komplette Anleitung gibt es hier [https://forum.odroid.com/viewtopic.php?f=158&t=31562](https://forum.odroid.com/viewtopic.php?f=158&t=31562) auf Englisch. Ich habe sie Schritt für Schritt befolgt und mir trotzdem noch mal notiert. Sieht kompliziert aus, ist aber eigentlich ziemlich einfach.

Erstmal alles herunterladen und installieren. Dazu werden die folgenden Dinge benötigt:

- Die aktuelle **Firmware** für den ODROID-GO (die .img-Datei nicht entpacken oder mounten):
  [https://github.com/OtherCrashOverride/odroid-go-firmware/releases](https://github.com/OtherCrashOverride/odroid-go-firmware/releases)
- **USB to UART Bridge VCP-Treiber** für macOS:
  [https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)
- **Homebrew** – Der fehlende Pakete Manager für macOS:
  [https://brew.sh/index_de](https://brew.sh/index_de)

Nachdem Homebrew und die Treiber erfolgreich installiert wurden, diese Zeilen im Terminal ausführen, um Python und das esptool zu installieren:

    brew install python3
    sudo easy_install pip
    sudo pip install esptool
    # und falls es später die Rückmeldung 'No module named esptool' gibt:
    sudo pip3 install esptool


Jetzt den ODROID-GO mittels eines USB-Kabels an den Mac anschließen und einschalten.

    ls /dev/cu.*
    # sollte u. a. /dev/cu.SLAB_USBtoUART zeigen


Jetzt in das Verzeichnis wechseln, in dem die Firmware gespeichert ist, z. B. so:

    cd ~/Downloads/firmware/


Vor dem Flashen sollte überprüft werden, ob das Gerät korrekt erkannt wird.

    python3 -m esptool  --port /dev/cu.SLAB_USBtoUART flash_id


Wenn alles gut läuft, dann sieht die Rückmeldung im Terminal etwa so aus:

    esptool.py v2.3.2-dev
    Connecting....
    Detecting chip type... ESP32
    Chip is ESP32D0WDQ6 (revision (unknown 0xe))
    Features: WiFi, BT, Dual Core, VRef calibration in efuse
    Uploading stub...
    Running stub...
    Stub running...
    Manufacturer: c8
    Device: 6018
    Detected flash size: 16MB
    Hard resetting via RTS pin...


Nun kann die Firmware installiert werden.

    # Beispiel für Firmware Version 20181001
    python3 -m esptool --chip esp32 --port /dev/cu.SLAB_USBtoUART --baud 921600 write_flash --flash_mode dio --flash_freq 40m --flash_size detect 0 odroid-go-firmware-20181001.img


Wenn der Vorgang erfolgreich war, sieht die Ausgabe im Terminal etwa so aus:

    esptool.py v2.3.1
    Connecting........_
    Chip is ESP32D0WDQ6 (revision (unknown 0xe))
    Features: WiFi, BT, Dual Core, VRef calibration in efuse
    Uploading stub...
    Running stub...
    Stub running...
    Changing baud rate to 921600
    Changed.
    Configuring flash size...
    Auto-detected Flash size: 16MB
    Compressed 301904 bytes to 146444...
    Wrote 301904 bytes (146444 compressed) at 0x00000000 in 3.1 seconds (effective 772.7 kbit/s)...
    Hash of data verified.
      
    Leaving...
    Hard resetting via RTS pin...


Nach der Aktualisierung startet der ODROID-GO neu und bootet direkt in die Firmware-Auswahl. Dort kann nun der Go-Play-Emulator oder andere Software installiert werden.


## Software für ODROID-GO

Hier sind meine persönlichen Favoriten, die ich auf meinem ODROID-GO habe.

### Emulatoren

- RetroESP32: [https://github.com/retro-esp32/RetroESP32](https://github.com/retro-esp32/RetroESP32)
- Go-Play: [https://github.com/OtherCrashOverride/go-play/releases](https://github.com/OtherCrashOverride/go-play/releases)
- c64-go: [https://github.com/Schuemi/c64-go/blob/master/README.md](https://github.com/Schuemi/c64-go/blob/master/README.md)
- Stella (Atari VCS 2600): [https://github.com/OtherCrashOverride/stella-odroid-go/releases](https://github.com/OtherCrashOverride/stella-odroid-go/releases)
- ProSystem (Atari 7800): [https://github.com/OtherCrashOverride/prosystem-odroid-go/releases](https://github.com/OtherCrashOverride/prosystem-odroid-go/releases)
- fMSXgo: [https://github.com/Schuemi/fMSX-go](https://github.com/Schuemi/fMSX-go)
- Super Go Play: [https://github.com/mattkj/super-go-play](https://github.com/mattkj/super-go-play)

### Spiele

- OpenTyrian: [https://github.com/jkirsons/OpenTyrian/tree/master/release](https://github.com/jkirsons/OpenTyrian/tree/master/release) (benötigt im Stammverzeichnis einen Ordner *tyrian*, der den Ordner *data* aus dem Archiv »Windows (x86) binary with Tyrian 2.1 data« enthält, das hier [https://bitbucket.org/opentyrian/opentyrian/wiki/Downloads.md](https://bitbucket.org/opentyrian/opentyrian/wiki/Downloads.md) heruntergeladen werden kann)
- Wolfenstein und Spear of Destiny: [https://github.com/jkirsons/wolf4sdl](https://github.com/jkirsons/wolf4sdl)
- Duke Nukem 3D: [https://github.com/jkirsons/Duke3D/tree/master/release](https://github.com/jkirsons/Duke3D/tree/master/release)

### Weitere ODROID-GO-Ressourcen

Hier gibt es eine schöne Zusammenstellung von Software- und Info-Links:
 [https://github.com/chrisdiana/awesome-odroid-go](https://github.com/chrisdiana/awesome-odroid-go).

