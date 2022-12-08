---
layout: article
language: de-DE
image: /images/...
title: Amiga 1000 Tastaturkabel-Mod
author: marc2o
---

Mein Amiga 1000 hat viele Jahre im Keller verbracht und ist auch schon einmal umgezogen, ohne seitdem wieder eingeschaltet worden zu sein. Tatsächlich ist ein Emulator in der heutigen Zeit deutlich komfortabler zu nutzen – und er benötigt auch weniger Platz.

Die [Tastatur des Amiga 1000](https://deskthority.net/wiki/Commodore_Amiga_1000) hat mir schon früher gefallen und das Gefühl beim Tippen mag ich noch immer. Leider kann man sie mit dem Originalkabel nirgends anschließen. Solche 4P4C-Stecker werden heutzutage wohl maximal noch für Telefonhörer und Headsets verwendet (wenn sie nicht eh kabellos sind). 

In [diesem Forum-Thread bei Amiga.org](https://forum.amiga.org/index.php?topic=71437.0) bin ich darauf gestoßen, dass man offenbar die Tastatur mit einem PS/2-Stecker verdrahten kann. 

Mit diesem neuen Kabel wäre die Tastatur dann auch kompatibel mit meinem geplanten C64-DTV-Mod. Stilecht auch, weil immerhin von Commodore, und auch praktisch, weil es sich bei meinem Modell um eine der frühen englischen Tastaturen handelt und somit kein »Keyboard Twister« für den C64-DTV nötig sein sollte.

## Einkaufsliste
* Telefonhörer-Spiralkabel mit RJ10-Stecker (4P4C), z. B. [dieses hier](https://www.amazon.de/gp/product/B000VN1E2E/ref=ppx_yo_dt_b_asin_image_o00_s00?ie=UTF8&psc=1).
* Sechspolige Mini-DIN Stecker (PS/2), z. B. [diesen hier](https://www.amazon.de/gp/product/B076H38ZRX/ref=ppx_yo_dt_b_asin_image_o02_s00?ie=UTF8&psc=1).

## Die Tastatur

<figure>
    <img src="https://deskthority.net/wiki/images/3/32/Commodore_Amiga_1000_keyboard_schematic.jpg" alt="Commodore Amiga 1000 Keyboard Schematic">
    <figcaption>Commodore Amiga 1000 Keyboard Schematic (<a href="https://deskthority.net/wiki/Commodore_Amiga_1000">Deskthority Wiki</a>)</figcaption>
</figure>

Alle Amiga Keyboard-Pinouts in einer Übersicht ([Quelle](http://www.l8r.net/technical/t-keyboard.shtml)):
```text 
Pin  A1000  A2/3000  A4000
 1   +5V    KLCK     I/O
 2   CLOCK  KDAT     n/c
 3   DATA   NC       Ground
 4   GND    GND      +5VDC (1000mA)
 5          +5V      Clock
 6                   n/c
```

Standard-PS/2-Pinout ([Quelle](https://en.wikipedia.org/wiki/PS/2_port)):
```text
Pin 1 DATA
Pin 2 not connected
Pin 3 GND
Pin 4 +5V
Pin 5 CLOCK
Pin 6 not connected
```

Nun ist allerdings der Haken, dass die Amiga-Tastatur ein eigenes Protokoll hat, das mit PS/2 nicht direkt kompatibel ist. Also muss ein Converter her, wie z. B. in diesem Arduino-Projekt: [Amiga 500/1000/2000 Keyboard Interface](https://forum.arduino.cc/t/amiga-500-1000-2000-keyboard-interface/136052).

