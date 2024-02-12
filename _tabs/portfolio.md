---
# the default layout is 'page'
icon: fas fa-book
order: 4
img_path: /assets/portfolio/
---

This page is a summary of most of the public software I have made or substantially contributed to. I've excluded most mods from it, to see them check out my [GameBanana page](https://gamebanana.com/members/submissions/sublog/1742760). If you want to see all of the programming stuff I've done, you can check out my [GitHub profile](https://github.com/AnimatedSwine37).

Unless otherwise specified, all of these projects are written in C# (it's a nice language).

(Sorry there aren't many pretty pictures, I don't do much GUI stuff)

## Aemulus Contributions
[Aemulus Package Manager](https://github.com/TekkaGB/AemulusModManager) is a mod manager for console Persona games which I have made contributions to ([full list](https://github.com/TekkaGB/AemulusModManager/pulls?q=is%3Apr+is%3Aclosed+author%3AAnimatedSwine37)) such as:
- [Auto updating](https://github.com/TekkaGB/AemulusModManager/pull/5)
- [Loadouts](https://github.com/TekkaGB/AemulusModManager/pull/17)
- [BF and BMD merging](https://github.com/TekkaGB/AemulusModManager/pull/23)

## Inaba Exe Patcher - ExPatches
[Inaba Exe Patcher](https://github.com/TekkaGB/Inaba-Exe-Patcher) is a framework originally made by [Tekka](https://github.com/TekkaGB) that allows other mods to patch P4G's exe on boot using a binary file. 
I extended it to use a plain-text format known as [ExPatches](https://github.com/TekkaGB/Inaba-Exe-Patcher/wiki/Ex-Patches) to make it easy for mods to inject assembly code or replace strings in any game's executable on boot. 
An example of a simple expatch that changes a hardcoded colour is:

```
const rColour = 255
const gColour = 255
const bColour = 255

[patch Persona Details Menu Patch]
pattern = FF 75 ?? FF 75 ?? FF 75 ?? 57 51 8B 4D ?? F3 0F 11 04 24 E8 ?? ?? ?? ?? F3 0F 10 45 ?? 83 C4 14
order = only
push {rColour}
push {gColour}
push {bColour}
```

This has now been used in many mods such as [Thieves Den Expanded](https://gamebanana.com/mods/482587), [Tiny Fixes 64](https://gamebanana.com/mods/422892), and [P4 Style Text Boxes](https://gamebanana.com/mods/389823). I also use it often for prototyping simple code mods.

## P3F Item Renamer
[P3F Item Renamer](https://github.com/AnimatedSwine37/P3FItemRenamer) is a command line tool for creating pnaches to rename items in Persona 3 FES. 

P3F has all item names hardcoded in its executable so to rename them pnach files are needed (PCSX2's patching format). This tool streamlines the creation of these files as they are tedious to manually create, requiring you to convert the name to hex characters and calculate the offset of it. An example of this is:

```
// Burger
patch=1,EE,207CB6D0,word,67727542
patch=1,EE,207CB6D4,word,00007265
```

With the tool, the user just enters the old and new names and the pnach is automatically created.

## Persona Event Message Editor
[Persona Event Message Editor](https://github.com/AnimatedSwine37/PersonaEventMsgEditor/) is a WiP interactive editor for event messages in Persona games. 

Normally messages would need to be decompiled to text files using [Atlus Script Tools](https://github.com/tge-was-taken/Atlus-Script-Tools) then recompiled and injected back into the game to see changes,  this tool simplifies the process by giving a real time preview of how changes will look. It also generally provides a more user friendly experience by stripping out boilerplate tags used in messages and allowing easy selection of bustups and voice lines. 

![Persona Event Message Editor Screenshot](PersonaEventMsgEditor.png)
_A screenshot of the WiP Persona Event Message Editor (excuse the ugly UI, functionality is a priority)_

This program is my first serious attempt at making a full GUI program using [Avalonia](https://github.com/AvaloniaUI/Avalonia) and the [MVVM pattern](https://learn.microsoft.com/en-us/dotnet/architecture/maui/mvvm).

## Unreal Essentials
[Unreal Essentials](https://github.com/AnimatedSwine37/UnrealEssentials) is a framework for replacing files in Unreal Engine game. 
I created it in the hopes of providing a universal way for people to mod Unreal Engine games that doesn't require putting files in the game's folder.

Files can be loaded loosely from mod folders due to a number of hooks I made to Unreal Engine code after studying the source and getting help from people who'd done it previously.
Additionally, loose files from UTOCs are possible thanks to integration with UTOC Emulator which [Rirurin](https://github.com/rirurin) created.
The combination of these should make it easier for people to create mods and minimise compatibility issues.

![Persona 3 Reload Essentials Thumbnail](P3REssentials.png)
_The thumbnail for [P3R Essentials](https://github.com/AnimatedSwine37/p3rpc.essentials), the main mod to utilise Unreal Essentials currently (thumbnail by [Lynn](https://twitter.com/lynlyn_cpk))_

Currently it's only really used by Persona 3 Reload through the [P3R Essentials](https://github.com/AnimatedSwine37/p3rpc.essentials) mod however, I hope more communities will pick it up in the future.

## Persona Modding Docs
The [Persona Modding Docs](https://animatedswine37.github.io/persona-modding-docs/) site is a community driven documentation project that I'm running. 
The aim of it is to create a centralised place to get information on modding all aspects of various Persona games as currently information is scattered between random discord channels and different websites if it's publicly available at all.

The site is hosted using [GitHub pages](https://pages.github.com/) with the [Just The Docs](https://github.com/just-the-docs/just-the-docs) [Jekyll](https://jekyllrb.com/) theme to build the site from markdown files.
It contains all the information needed for anyone, regardless of prior knowledge, to add to the site and submit changes with a pull request in the hopes of getting as many contributors as possible.

It being fully open-source also means, should I ever stop maintaining it, anyone else could pick up the project, protecting the information in it.


## File Emulation Framework Contributions
[File Emulation Framework](https://github.com/Sewer56/FileEmulationFramework) is a framework made by [Sewer56](https://github.com/Sewer56) that allows mods to "emulate" files, mainly for the sake of allowing multiple mods to edit the same file without causing conflicts. The framework relies on "emulators" to actually make this happen for a specific file type, I've contributed two so far:

### PAK Emulator
[PAK](https://amicitia.miraheze.org/wiki/PAC) files are archives, commonly used in the games to group together related files. 

[PAK Emulator](https://sewer56.dev/FileEmulationFramework/emulators/pak.html) was initially developed by [Lt. Sophia](https://github.com/LTSophia) but then picked up by me when she was no longer able to work on it. 
It lets multiple mods edit files inside of a single archive without conflicts by creating a stream that emulates a pak file with all of the changes merged. The majority of the hard work for this was done by Sophia but I also did a lot of work cleaning it up and making it integrate properly with [Persona Essentials](https://github.com/Sewer56/p5rpc.modloader).

### BF Emulator
[BF](https://amicitia.miraheze.org/wiki/BF) files are compiled code files which contain much of the game's logic. They are a propriery format that can be decompiled to source code (called Flowscript) and recompiled using [TGE](https://github.com/tge-was-taken)'s [Atlus Script Compiler](https://github.com/tge-was-taken/Atlus-Script-Tools).

[BF Emulator](https://sewer56.dev/FileEmulationFramework/emulators/bf.html) lets multiple mods edit different procedures in the same BF file by running provided source code through Atlus Script Tools to create a merged file. This both improves compatibilty and makes it easier to create Flowscript mods since source code is automatically compiled on launch instead of needing to be manually compiled by the creator (it gets very tedious doing it manually).
