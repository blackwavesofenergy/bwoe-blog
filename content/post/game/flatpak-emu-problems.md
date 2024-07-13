+++
title = 'Flatpak Emu Problems of March 2024'
date = 2024-03-03T18:09:36Z
draft = false
tags = ['game-stuff',]
+++

So recently, there was some bizarre emulation problems. The issue didn't come with the Steam Deck, or EmuDeck, but with the emulators themselves, specifically the Flatpak version commonly used in Linux.

Dolphin, RPCS3, and Citra all were nonfunctional out of nowhere. Citra was quickly patched, but Dolphin and RPCS3 are still unable to boot as of this post. Booting them reveals no error message or dumped log. Booting them via CLI (i.e. ```flatpak run org.DolphinEmu.dolphin-emu```) gives you the following message:
```
dolphin-emu: symbol lookup error: dolphin-emu: undefined symbol: _Zls6QDebugRK11QDockWidget, version Qt_6
```
The issue seemed to be with [Qt](https://archlinux.org/todo/qt-662-abi-break/) and a Flatpak update that breaks the application. It goes to show the vulnerability of projects like this when a simple symbol incompatibility renders all yours games unplayable. 

You read the GitHub issue I opened here:

https://github.com/flathub/org.DolphinEmu.dolphin-emu/issues/189