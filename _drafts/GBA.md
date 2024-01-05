---
layout: article
language: de-DE
image: /images/...
title: Game Boy Advance SP
author: marc2o
tags:
- Game Boy Advance SP
- Nintendo
- Gaming
- Console
- Modding
- Game Development
---

## Game Dev

Learn:
- https://exelo.tl/goodboy-advance.html
- https://www.coranac.com/tonc/text/
- https://problemkaputt.de/gbatek.htm
- https://ianfinlayson.net/class/cpsc305/notes/06-gba1
- https://kylehalladay.com/blog/tutorial/gba/2017/03/28/GBA-By-Example-1.html

[Arm GNU Toolchain](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain)

🛑 DO NOT USE: `brew install arm-none-eabi-gcc` Diese Version hat keine Include-Dateien, wie z. B. `stdint.h`.
✅ INSTEAD USE: `brew install --cask gcc-arm-embedded`, ist identisch mit der Installation von developer.arm.com.

natu
https://natu.exelo.tl/
https://git.sr.ht/~exelotl/natu-examples/tree/master/item/goodboy_gallery/source/simple_anim.nim

```bash
brew install arm-none-eabi-gcc
brew install nim
nimble install https://git.sr.ht/~exelotl/natu@0.2.0
```
Nim x SDL2
`nimble install sdl2`
https://hookrace.net/blog/writing-a-2d-platform-game-in-nim-with-sdl2/
https://nim-lang.org/documentation.html
https://nim-lang.org/docs/tut1.html

GBA Bootstrap
https://github.com/AntonioND/gba-bootstrap

Meson Build System (https://mesonbuild.com) `brew install meson`

gba-toolchain – CMake based toolchain for GBA homebrew development
- https://github.com/felixjones/gba-toolchain
- https://felixjones.github.io/gba-tutorial/

sdk-seven – Modern GBA Software Development Kit
(https://github.com/LunarLambda/sdk-seven)

Download https://github.com/LunarLambda/sdk-seven/releases

```bash
./setup.sh
ninja -C build
```

Help `#sdk-seven` on [Discord](https://discord.io/gbadev)

## Modding

[Nintendo Gameboy Advance SP Modded Console, Translucent Purple Edition. IPS V3, USB C, Audio Enhanced Build To Order with Custom Black Buttons.](https://shopmodernmods.com/collections/nintendo-gameboy-sp/products/nintendo-gameboy-advance-sp-modded-console-translucent-purple-edition-ips-v2-usb-c-audio-enhanced-build-to-order-w-custom-buttons?variant=40302993473705)

[EVERDRIVE GBA MINI, Transparent Clear](https://everdrive.me/cartridges/everdrive-gba-mini.html)

[Game Boy Advance SP Schutzhülle (Transparent)](https://www.silentmodding.com/de/game-boy-advance-sp-schutzhulle-transparent.html)

[Game Boy Advance 2 Player Link Cable](https://www.retronintendokaufen.de/gameboy/gameboy-advance-gba/link-kabel)

[Game Boy Advance SP Headphone Jack Adapter](https://www.retronintendokaufen.de/gameboy-advance-gba/gameboy-advance-sp-headphone-jack-adapter)

[EverDrive GBA Theme Editor](https://orangeglo.github.io/everdrive-gba-editor/)