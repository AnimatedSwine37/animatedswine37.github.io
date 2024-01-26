---
layout: post
title: What will P3R modding be like on day one
date: 2024-01-26 16:20 +1000
toc: true
---
With Persona 3 Reload coming out in a week (as of writing) there has been lots of speculation as to whether it will be moddable and what that will be like. 
This post aims to give the most accurate answers to these questions given the current information we know. 

Note that whilst I've done my best, I'm not psychic, everything should be taken with a grain of salt until the game is actually in our hands.

> **tldr**;
> - Reloaded will be used for P3R mods utilising the new Unreal Essentials mod. 
> - UTOC signatures are not a problem, any UTOC or PAK files should be loadable day one (or very soon after).
> - All common types of mods should be possible, some may take longer to make as we get used to the tools.
> - Don't harass modders, we want to play the game too.
{: .prompt-info }


## What mod loader will we use?
Traditionally Unreal Engine games either use no modloader, requiring users to manually place files in the game's folder, or use [Unverum](https://github.com/TekkaGB/Unverum). In contrast, the mainline PC Persona games have used [Reloaded](https://reloaded-project.github.io/Reloaded-II/). To keep things consistent I am working to ensure we will be able to use Reloaded for P3R as well.

To this end, I am currently working on [Unreal Essentials](https://github.com/AnimatedSwine37/UnrealEssentials), a mod that, like [Persona Essentials](https://github.com/Sewer56/p5rpc.modloader), will be a framework to allow other mods to replace files. As I have only been working on this for a short time, it may not be fully cooked by launch as such there are two possibilies for mod loading:

### UTOC Emulator (The Good Ending)
UTOC Emulator is something that both Rirurin and I are separately working on. If either of us finish our versions of it, mod makers will be able to place files (uassets, uexps, ubulks) loosely in their mods instead of needing to make UTOC files. If this happens, there should be no problems with conflicting chunk ids and it should generally be a nicer experience for mod makers.

Even though we have access to the [Unreal Engine source](https://docs.unrealengine.com/5.3/en-US/downloading-unreal-engine-source-code/), which helps a lot, making a file emulator is still a large task. As such there is a real possibility that UTOC emulator will not be complete in time, in this case people will have to build their own UTOC files and loose loading will be added later when the emulator is ready.

### Full UTOC Loading (The Not As Good Ending)
All is not lost if UTOC Emulator is not complete by launch. The current version of Unreal Essentials already adds the ability to load UTOC and PAK files from Reloaded mods. This means creators will be able to make full UTOC or PAK files using existing tools and load them by putting them in a Reloaded mod.

Essentially this means mods will be made the same way you would for any Unreal Engine game that uses UTOC files but instead of manually placing files in the game's folder, or using [Unverum](https://github.com/TekkaGB/Unverum), you will make a Reloaded mod and put the same files in there. The key difference between Reloaded and other methods is no files are ever put into your game's folder, files are loaded **directly** from the Reloaded mod.

## What about UTOC signatures?
Often games prevent modded files from being loaded by requiring the files to match a signature, in these cases a patch must be made to disable this signature check. Unreal Essentials already removes these signature checks so this is not a concern, any files should work.

## What types of mods will be possible?
In general, any kind of mod that you'd see in an Unreal Engine game should be possible for P3R and should be made in roughly the same way. Examples of these types of mods include:
- Model Mods
- Texture Mods
- Text Mods
- Music Mods
- Ligthing Mods 

### Music Mods
As [reported by MeovvCAT](https://x.com/osu_MeovvCAT/status/1750113534732562733?s=20), P3R is confirmed to use Criware middleware which is a common middleware used to play videos and audio. 

We do not know for certain whether it will actually be used for audio (it could just be for video), but if it is, music modding should feel familiar as the mainline games all also use Criware for audio. If it's not being used this does not mean music modding is dead, it will just be different.

### Script Mods
In the mainline games Atlus has so far used a proprietary scripting format known as Flowscript. This is used to control much of the game's logic such as interactions with npcs, parts of events, and battle AI.

It is possible that flowscript is also used in P3R, however there is also the possibility that Unreal Engine's blueprints system is used instead. If flowscript is still used then Atlus Script Tools will likely be quickly updated to support it, making script mods possible early on. In the case the blueprints or some other system is used it will likely be much longer before you see such mods as creators have to learn how to use them.

### Code Mods
Code mods are those that change the game's executable to change features that are hardcoded. These will definitely be possible (Unreal Essentials is a code mod) but how necessary they actually are (in their traditional form) is not known. If the game uses blueprints heavily it is possible that we will be able to edit them instead of having to edit the exe.

A tool that could be greatly helpful for code mods is [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS), a scripting system for Unreal Engine games that gives easy access to UE objects from C++ or Lua code. An API for C# is also being worked on by [Ryn](https://twitter.com/WistfulHopes) which, when done, will make it easy to use with Reloaded code mods. 

We'll have to wait until people (like myself) actually start writing code mods to see how they're used, but in general the sky is the limit with them (given enough time and effort).

## How are these tools being made already?
The patches that Unreal Essentials applies hook functions that are a part of Unreal Engine. As this code does not change between games using the same engine version we can find it "universally" using [signature scanning](https://reloaded-project.github.io/Reloaded-II/CheatSheet/SignatureScanning/). 

Unreal Essentials has been tested against games with unreal engine versions 4.25 to 4.27 so as long as P3R uses one of these versions it should immediately work. If it turns out a custom version is being used (as some games like Hi-Fi Rush do) it should still be relatively easy to find the necessary signatures as Ghidra's new [BSim](https://github.com/NationalSecurityAgency/ghidra/tree/master/GhidraDocs/GhidraClass/BSim) feature makes it easy to find similar functions between different progarms. This should hopefully only delay mod loading for a few hours (a few days absolute worst case).

## When will X mod be made?
Even if peoeple have the ability to make mods on day one (or very soon after), that does not necessarily mean many mods will be released that soon. 

Most mod makers probably want to actually play the game so please be patient. Do not harass modders to create something, if there is something that you want that desperately then consider making it yourself instead. 

With this new Engine there will be a bit of a knowledge reset and I, and others, will be aiming to create better documentation for modding so making stuff yourself should be more achievable (this will of course take time).

## How can I stay up to date?
The best place to keep up to date on major P3R modding news is the [Persona Modding Discord Server](https://discord.gg/naoto). 
