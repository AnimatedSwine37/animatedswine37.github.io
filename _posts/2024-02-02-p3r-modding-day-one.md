---
layout: post
title: P3R Modding Day One Is Here
date: 2024-02-02 00:23 +1000
toc: true
---
Persona 3 Reload is now out so I've put together some information on how we'll mod it on day one and in the future. This is essentially an update to my [Before Day One post](/posts/p3r-before-day-one) from earlier utilising the new information we now have.

> **tldr;**
> - The tools needed for modding will be publicly ready in the next few days, please be patient.
> - [Unreal Essentials](https://github.com/AnimatedSwine37/UnrealEssentials) will be used to loosely load files with [Reloaded](https://reloaded-project.github.io/Reloaded-II/)
> - UTOC signatures are not a problem, all files can be replaced
> - Every type of mod should be possible, some may take longer as people learn new tools
> - Common Atlus file types such as BMD, BF are used in the game alongside UE files like blueprints.
> - Criware is used for music so making those mods should be very familiar
> - Give modders time, we want to play the game too
{: .prompt-info }

## When will modding tools be ready? (READ THIS!!!)
This is the big question and the answer is, in the next few days. Note that I am purposely leaving this a bit vague to give us time, hopefully it will be sooner rather than later.

Whilst we've worked hard to prepare the tools in time, there are still some final things to do before they are ready for the public. We don't want to release something half baked so please be patient.

In the meantime you can use standard Unreal Engine tools to extract files and start looking into things if you'd like. (I'm not going to elborate more than that, if you already know what to do then go for it, otherwise please be patient and specific guides will come soon.)

> Everything below will be true **when the tools are ready** not neccessarily right now (I will update this when that happens).
{: .prompt-warning }


## What mod loader will we use?
Traditionally Unreal Engine games either use no modloader, requiring users to manually place files in the game's folder, or use [Unverum](https://github.com/TekkaGB/Unverum). In contrast, the mainline PC Persona games have used [Reloaded](https://reloaded-project.github.io/Reloaded-II/). To keep things consistent, we will be using Reloaded for P3R.

To this end [Unreal Essentials](https://github.com/AnimatedSwine37/UnrealEssentials) has been created. It is a mod that, like [Persona Essentials](https://github.com/Sewer56/p5rpc.modloader), acts as a framework to allow other mods to replace files. 
With it, mods can replace files in both UTOCs and PAKs loosly (i.e. you never have to make a UTOC or PAK yourself). This also means that existing file emulators like BF Emulator and AWB Emulator will work with the game, allowing for greater compatibilty when multiple mods edit the same file of certain types.

### What about UTOC signatures?
Often games prevent modded files from being loaded by requiring the files to match a signature, in these cases a patch must be made to disable this signature check. Unreal Essentials already removes these signature checks so this is not a concern, any files should work. This also means that you can actually use full PAK or UTOC files if you want, although there shouldn't really be a need to do that.

## What types of mods will be possible?
In general, any kind of mod that you'd see in an Unreal Engine game should be possible for P3R and should be made in roughly the same way. Examples of these types of mods include:
- Model Mods
- Texture Mods
- Text Mods
- Music Mods
- Ligthing Mods 

To make most types of mods creators will need to download Unreal Engine 4.27 which will be a substantial change in workflow from previous games. Because of this, you should expect people to take some time whilst they learn the new tools.

### Music Mods
P3R uses Criware middleware which for its music which is what the mainline games have all used. This means music modding should be relatively easy to do, particularly if you've done it on the past PC Persona games. 

### Script Mods
In the mainline games Atlus has so far used a proprietary scripting format known as Flowscript. This is used to control much of the game's logic such as interactions with npcs, parts of events, and battle AI.

P3R uses BF files in many places meaning, once Atlus Script Tools is updated, script mods should be easy to make, particularly if you've made them before. However, the game also includes many blueprint files so it is possible things that were preeviously up to flowscript now use blueprints. We'll need to wait for moddders to dig deeper into the files to work out where exactly each are used.

### Code Mods
Code mods are those that change the game's executable to change features that are hardcoded. These are definitely possible but will likely be easier to make as blueprints may be used in some things that were previously hardcoded.

In the cases where things are still truly hardcoded [UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) should greatly help in making code mods. It is a scripting system for Unreal Engine games that gives easy access to UE objects from C++ or Lua code with a C# version in the works that will fit well with the normal code mod workflow. 

We'll have to wait until people (like myself) actually start writing code mods to see how they're used, but in general the sky is the limit with them (given enough time and effort).

## What about Game Pass?
As was the case with the other games that were on Game Pass, modding will be possible, but harder to do and potentially more limited. This is because the Game Pass version has a different executable with DRM that is built into Windows, adding some complexity to getting anything working at all with it.

If you can afford it, you're going to have a much better time modding with the Steam version of the game.

## When will X mod be made?
Even if people have the ability to make mods on day one (or very soon after), that does not necessarily mean many mods will be released that soon. 

Most mod makers probably want to actually play the game so please be patient. Do not harass modders to create something, if there is something that you want that desperately then consider making it yourself instead. 

With this new Engine there will be a bit of a knowledge reset so I, and others, will be aiming to create better documentation for modding so making stuff yourself should be more achievable (this will of course take time). One of the places this documentation will hopefully be is on the (currently very WiP) [modding docs](https://animatedswine37.github.io/persona-modding-docs/).

## How can I stay up to date?
The best place to keep up to date on major P3R modding news is the [Persona Modding Discord Server](https://discord.gg/naoto). 
