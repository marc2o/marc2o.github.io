---
layout: article
language: de-DE
image: /images/*.jpg
title: Emulation auf dem Steam Deck
author: marc2o
tags:
- emulation
- steam deck
- gaming
---

Das Steam Deck ist nicht nur eine hervorragende handheld Spielkonsole, sondern auch erstklassig geeignet für Emulation.

<!--more-->

… 

---

Inhalt:

- [Speicherorte](#speicherorte)
- [Box Art](#box-art)

---

## Speicherorte

…

## Box Art

https://www.steamgriddb.com/game/36566

## Beyond Good & Evil (Nintendo GameCube)

Eigener Shader, um die Letterbox zu zoomen…

```cpp
void main() {
    float2 coords = GetCoordinates() - float2(0.50f, 0.50f);
    float2 new_coords = float2(coords.x, coords.y*3.0f/3.6f);
    float2 sample_coords = new_coords + float2(0.50f, 0.50f);
    SetOutput(SampleLocation(sample_coords));
}
```

Config für das Spiel…

```toml
# GGEE41, GGEP41, GGEY41 - Beyond Good and Evil

[Video_Settings]
AspectRatio = 3
wideScreenHack = False

[Video_Enhancements]
PostProcessingShader = bge_remove_letterbox

[Video_Hacks]
ImmediateXFBEnable = False
```

## Guides und Tools

https://retrogamecorps.com/2022/10/16/steam-deck-emulation-starter-guide/

