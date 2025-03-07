---
permalink: /nes/
layout: post
console: nes
title: Nintendo Entertainment System Reverse Engineering
consoleimage: /public/consoles/Nintendo Entertainment System.png
thumbnail: /public/consoles/Nintendo Entertainment System.png
image: /public/images/nes/NES Reversing.jpg
twitterimage: https://www.retroreversing.com/public/images/nes/NES Reversing.jpg
breadcrumbs:
  - name: Home
    url: /
  - name: Consoles
    url: /
  - name: Nintendo Entertainment System
    url: #
recommend: nes
recommendTitle: All NES Posts
editlink: ../categories/consoles/nes.md
updatedAt: '2022-10-08'
---

# Introduction
Interested in learning more about the the NES? Excellent! This section will guide you through the basics, starting from basic assembly language all the way to an introduction to reverse engineering your first game!

---
# Games

## Official Retail NES Game Source Code
If you are interested to see officially released or leaked source code check for the Nintendo Entertainment System check out our other post:
{% include link-to-other-post.html post="/source-code/retail-console-source-code" description="For the official source code check out this post." %}

### Home Alone NES Source Code
The full source code for the NES game **Home Alone** was released online thats to the **Game History Org** and we have a specific post covering the details of the files included:
{% include link-to-other-post.html post="/home-alone-2-nes-source-code/" description="For the official source code to Home Alone for the NES check out this post." %}

---
## Reverse Engineered NES Games
If you are interested to see existing reversing projects for the NES check out our other post specifically on this topic:
{% include link-to-other-post.html post="/source-code/decompiled-retail-console-games" description="For the list of decompiled games check out this post." %}

## Super Mario Bros
The original Super Mario Bros was the game that revolutionised platformers, with its smooth scrolling and excellent game design there was bound to be many reversing projects related to it. This section covers projects specifically targeted towards the classic platformer.

### Super Mario Compiler
The website **neilb.net** has created what it calls a **Mario Compiler** which takes in the original Super Mario Bros ROM and disassembles it.
The disassembled code is then shown to the user and can then be modified and re-assembled back into a working NES ROM. All from within the web application!

{% include link-to-other-site.html url="https://neilb.net/mariocompiler/" description="Check out the Mario compiler here" image="" title="Mario Compiler"  %}

You can also view the source code for the project here: [nbarkhina/MarioCompiler: A Super Mario Compiler written in JavaScript](https://github.com/nbarkhina/MarioCompiler)

### Super Mario Bros in C
**Mitchell Sternke** has created an impressive port of the original NES Super Mario Bros, he has written a tool that converts most of the 6502 assembly code into its equivalent C code. He has then written a PPU, Controller and APU emulation layer in C to make it all work into a portable C application running natively on the target hardware (No 6502 CPU emulation required!).

You can find it on Github here:
[SuperMarioBros-C/README.md at master · MitchellSternke/SuperMarioBros-C](https://github.com/MitchellSternke/SuperMarioBros-C/blob/master/README.md)

---
# Hardware

## Development Kit Hardware
Since Nintendo were very new to the home video game market, they saw themselves as creating most of the software that will run on the NES. 
So they did not make a public NES development kit, so most third parties has to roll their own development kits.

We have a specific post covering all the NES development kits that we know about here:
{% include link-to-other-post.html post="/famicom-nes-development-kit/" description="For information about Nintendo's Famicom development hardware check out this post." %}

## Retail NES Hardware
For an in-depth look at the NES Retail hardware architecture check out the excellent post by **Copetti.org**:
{% include link-to-other-site.html url="https://www.copetti.org/writings/consoles/nes/" description="Copetti.org has an excellent tear down of the NES Hardware and how it works" image="/public/consoles/Nintendo Entertainment System.png" title="Nintendo Entertainment System (NES) Architecture - A Practical Analysis" %}

## Retail NES Controller Electronics
<section class="postSection">
    <iframe class="wow slideInLeft postImage" width="560" height="315" src="https://www.youtube.com/embed/dahbvSYV0KA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<div markdown="1">
Have you ever wondered about how a NES controller actually works, such as the circuits and electronic components used to physically create it? 
  
  Well you are in luck, the YouTuber **Displaced Gamers** explains exactly how the electronics of the NES controller works and a few interesting facts along the way!
  
He opens up the NES controller revealing the physical wires, traces (green lines on the circuit), rubber membranes and the 8-bit shift register (HD14021BP).
  
  The Controller as with all electronics has both a Power (High) and Ground (Low) lines, with 5V used for Power. Ground is connected to all of the buttons including the 4 D-pad buttons, whereas the Power lines go straight to the Carbon Printed Pull-Up resistors which then in-turn goes to each of the buttons. 
  
  When a button is pressed it completes the circuit at that point meaning it is pulled Low (Grounded) which allows the shift register to know that button is pressed. The resistors are used to make sure the power lines are always High, so we can ensure that when a pin is pulled low it has definitely been pressed.
</div>
</section>

---
# Software Development
There was no official software development kit provided by Nintendo for the NES, instead developers were required to either get an off-the-shelf 6502 assembler or write their own. Paired with a booklet covering how the NES handled graphics, input and sound, this was all that game developers got in terms of software for game development on the NES.

Nowadays there are many open source assemblers, IDE's and even high level language compilers that can be used to create NES homebrew games.

## What is an emulator and how does it work?
We have a specific post covering exactly how emulators work including tips for writing your own emulators: 
{% include link-to-other-post.html post="/how-emulators-work" description="For more information on how emulators work check out this post." %}

## NES Emulators with Debugging Functionality
When reversing or developing NES games it is vital to use a good emulator which has debugging support such as:
* **BreakPoints** - e.g can create a breakpoint at a specific code or memory location and execution will stop at that place
* **Symbol File support** - e.g supports loading a file with a list of known variable and function names
* **Built-in Assembler** - assemble code in real-time within the emulator to quickly create patches
* **PPU Viewer** - see the current state of the Picture Processing Unit such as the Nametable, Sprites, CHR Memory viewer etc

Here is a list of a few Open Source emulators that have some of these features:
* **Mesen** - [SourMesen/Mesen: Mesen is a cross-platform (Windows & Linux) NES/Famicom emulator built in C++ and C#](https://github.com/SourMesen/Mesen)
* **Nintendulator** - [quietust/nintendulator: NES emulator for Windows](https://github.com/quietust/nintendulator)

## The Making of ROM City Rampage (Grand Theftendo)
The developers of **Retro City Rampage** (V-blank Entertainment) created a limited NES port of their game for the NES and documented some of the major changes that they needed in order to get it to run on the real console:
<iframe width="560" height="315" src="https://www.youtube.com/embed/Hvx4xXhZMrU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

This is a good introduction to some of the limitations you need to think about when developing a NES game. According to **RomHacking.net**[^1] they were not allowed to release the NES ROM created for **Grand Theftendo** or even some of the documentation that they wrote while creating it. However the ROM is in the final game, so if you own the game it is possible to extract the NES ROM and play it in an emulator!

You need to use a tool called **BFP Extractor** to extract content from: the file **gamedata.bfp** at addresses 0x747E67D6 and 0xC87FC3A3 then create a iNES ROM Header for it with the following Hex values:
```
4E 45 53 1A 20 20 50 00 00 00 00 00 00 00 00 00
```
Then simply join the header with the content from address 0x747E67D6 and 0xC87FC3A3 together and name it as a .nes file.

---
# Game Modding

## Cheat Cartridges (Game Genie)
The main cheat cartridge available for the NES was the **Game Genie** created by **Codemasters** (Distributed by Galoob & Hornby Hobbies). This was a physical connector that would sit between the NES and the Game Cartridge you wanted to cheat on. It would alter the signals based on which memory addresses were being read/written to in real-time based on the Cheat code that was loaded into the system.

### Game Genie Code Format
The Game Genie used a special encoding format for its codes which can be encoded and decoded using this handy online tool:
[Game Genie Encoder/Decoder](https://games.technoplaza.net/ggencoder/js/)

### Making Game Genie Codes Permanent
If you want to permanently modify one of your NES ROM files with a certain cheat code there is a Windows Only tool to do this created by **rdurbin**: 
[Romhacking.net - Utilities - Permanent Game Genie](https://www.romhacking.net/utilities/784/)

## NES Memory Corruption
Corrupting the memory of a ROM has become very popular over on Youtube with creators such as **Vinesauce** regularly using ROM corruptors on popular games to produce some interesting results.

If you want to try it yourself we recommend the **Real-Time Corruptor Vanguard** (RTCV) available on Github: [redscientistlabs/RTCV: Real-Time Corruptor, Vanguard, CorruptCore, NetCore2 https://redscientist.com/rtc](https://github.com/redscientistlabs/RTCV). It is written using DotNet so it should work on Windows and MacOSX/Linux via Mono.

For more information we have a specific post on the topic of Game memory corruption:
{% include link-to-other-post.html post="/emulator-game-memory-corruption" description="For information about Game Memory Corruption check out this post." %}

### Deliberate NES Memory Corruption by Javidx9
The Youtuber **Javidx9** has created a system that randomly corrupts the memory of a NES game (every 5 seconds) as it runs just for the fun of seeing the chaos that follows. The interesting part of this is that his system is somewhat smart in that it tracks the most common memory addresses used per frame (excluding screen memory) and changes those at a higher rate compared to just random memory locations.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-csXgGstvHg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Apparently the source code was once linked on the twitch page, but it is sadly so old now that the link has disappeared, it would have been really interesting to see it!

## HD Texture Packs
You can easily replace the 2D Sprites and Tiles from a NES game with HD/4K alternatives using specific emulators such as Mesen and HDNes. The gameplay is unchanged as it overlays the HD Graphics on top of the game and doesn't have any of the colour limitations of the NES hardware. These modifications as emulator specific and will not modify the original ROM.

Mesen even comes with a HD Pack Builder Tool to create your own texture packs, for more information: [HD Packs :: Mesen Documentation](https://www.mesen.ca/docs/hdpacks.html#using-the-hd-pack-builder)

---
# Graphics & Rendering
For an introduction to how the NES renders graphics to the screen checkout **Austin Morlan**'s excellent article on his website:
[An Overview of NES Rendering - Austin Morlan](https://austinmorlan.com/posts/nes_rendering_overview/).

It covers the following topics related to NES Graphics:
* **Tiles** - 8x8 pixel graphics used to make up the background of a game
* **Block** - A set of 4x4 tiles (used for colour indexing)
* **Frames** - Background made up of 32x30 titles (256x240 pixels)
* **Nametable** - Big blob of bytes, specifying which tile is placed where in the frame (Like a Room in GameMaker)
* **Pattern Table** - Contains the actual pixels for the 8x8 tiles as either a 1 or a 0 (no colour information)
* **System Palette** - A Palette of all the 64 colours a NES can output to the screen
* **Frame Palette** - A dynamic subset of the System Palette of just the colours used in a single frame. Palette 0 to 3 are for background tiles, and 4 to 7 are for sprites.
* **Attribute Table** - A look up table of which Palette to use for that Block (set of 4x4 tiles)
* **Sprites** - Graphics made up of tiles but are rendered above the background tiles

---
# Reverse Engineering

## File Formats
When reversing NES games you will come across a variety of file formats, this section will try to cover all of the most common formats you will encounter.

The formats for NES ROMS (virtual cartridges) are:
* **.NES** - This is the most common format for NES ROMs to be in, it is also known as the **iNES** format, most emulators will play this format (For More information: [INES - NESdev Wiki](https://www.nesdev.org/wiki/INES))
* **.UNIF** - The Universal NES Image Format was a competitor format to iNES 1.0 but has largely been replaced by iNES 2.0
* **.FDS** - Famicom Disc System backup format created for the **fwNES** emulator
* **.NSF** (NSF2/NSFe) - NES Sound Format for playing music ripped from NES games can be played back in some emulators and specific NSF tools.
* **.TNES** - Official Format by Nintendo used on the 3DS Virtual Console and also supports Famicom Disc System games

## Tutorial - Adding Hard Drops to NES Tetris
The website **Grid Bugs** has written an excellent article on reverse engineering the NES version of Tetris to add functionality to the game called a **Hard Drop**. Check it out here:
[Reverse-Engineering NES Tetris to add Hard Drop](https://www.gridbugs.org/reverse-engineering-nes-tetris-to-add-hard-drop/)

---
# All Posts
<div>

{% include console.html %}
</div>

---
# References
[^1]: [ROM City Rampage](https://www.romhacking.net/forum/index.php?topic=15982.0)
