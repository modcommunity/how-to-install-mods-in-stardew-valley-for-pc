A guide on how to **download** and **install mods** in **Stardew Valley** on PC. We cover all three of the common methods: installing mods by hand (which is the standard way for this game), [Vortex](https://www.nexusmods.com/about/vortex/) (the mod manager from [Nexus Mods](https://www.nexusmods.com/stardewvalley)), and the [CurseForge app](https://www.curseforge.com/download/app).

This guide is focused on **Windows**, but Stardew Valley mods work on **Linux** and **macOS** too, and we've noted the differences where they matter.

[**View Guide On TMC (Recommended Due To Better Formatting)**](https://moddingcommunity.com/blog/how-to-install-mods-in-stardew-valley/)

Stardew Valley is one of the friendliest games there is to mod. There's no load order to fight with, no plugin limit, no archive invalidation, and nothing to patch. Almost every mod is a folder you drop into one place, and the game tells you in a console window whether it loaded.

There is exactly one thing you need to get right first, and that's **SMAPI**. It's the loader that makes mods possible at all, and pretty much every mod on Nexus depends on it. We'll install SMAPI, then install [Tractor Mod](https://www.nexusmods.com/stardewvalley/mods/1401) by **Pathoschild** on top of it as our example mod, through each of the three methods.

## Table Of Contents
* [Requirements](#requirements)
* [Game Version Notes](#game-version-notes)
    * [Running Mods On Linux & macOS](#running-mods-on-linux--macos)
* [Back Up Your Saves!](#back-up-your-saves)
* [What Is SMAPI?](#what-is-smapi)
* [Installing SMAPI](#installing-smapi)
    * [Downloading SMAPI](#downloading-smapi)
    * [Running The Installer](#running-the-installer)
    * [Setting Up The Steam Launch Option](#setting-up-the-steam-launch-option)
    * [Launching The Game](#launching-the-game)
* [Where To Download Mods](#where-to-download-mods)
* [The Mod We're Installing](#the-mod-were-installing)
* [Installing Mods Manually](#installing-mods-manually)
    * [Downloading The Mod](#downloading-the-mod)
    * [Extracting And Copying](#extracting-and-copying)
* [Installing Mods Through Vortex](#installing-mods-through-vortex)
    * [Managing Stardew Valley In Vortex](#managing-stardew-valley-in-vortex)
    * [Letting Vortex Install SMAPI](#letting-vortex-install-smapi)
    * [Installing A Mod](#installing-a-mod)
    * [The Mods Page](#the-mods-page)
    * [Launching Through Vortex](#launching-through-vortex)
* [Installing Mods Through The CurseForge App](#installing-mods-through-the-curseforge-app)
* [Checking If Your Mods Loaded](#checking-if-your-mods-loaded)
* [Updating & Removing Mods](#updating--removing-mods)
* [Other Useful Mods](#other-useful-mods)
* [Troubleshooting](#troubleshooting)
* [Notes](#notes)
    * [Multiplayer](#multiplayer)
    * [Mod Config Files](#mod-config-files)
* [See Also!](#see-also)
* [Conclusion](#conclusion)

## Requirements
* A PC copy of Stardew Valley (this guide uses the **Steam** version).
* [7-Zip](https://www.7-zip.org/) or any other archive extraction software.
* A free [Nexus Mods](https://www.nexusmods.com/stardewvalley) account (optional, but you'll want one).
* A basic understanding of copying and moving folders around.

## Game Version Notes
Stardew Valley is at version **1.6.x** at the time of writing, and mod compatibility is generally excellent. The version matters less here than in most games, but two things are worth knowing.

* **SMAPI has to match your game version.** When the game updates, SMAPI updates within a day or two and you install the new one. This is normally painless.
* **Mods can lag behind.** Individual mods sometimes need a few days to catch up after a big update. The [SMAPI mod compatibility list](https://smapi.io/mods) tracks which mods currently work, which is the fastest way to check before you update.

Steam, GOG and the Xbox Game Pass PC versions all support mods. The **Microsoft Store / Game Pass** version needs a couple of extra steps that [smapi.io/install](https://smapi.io/install) covers, because of how Windows protects the install folder.

### Running Mods On Linux & macOS
Stardew Valley is rated **Platinum** on [ProtonDB](https://www.protondb.com/app/413150) and there's a native Linux build, so this is one of the easier games to mod outside Windows.

SMAPI ships installers for all three platforms in the same download - `install on Windows.bat`, `install on Linux.sh` and `install on macOS.command`. Run the one for your system and everything else in this guide works the same way.

**NOTE** - On Linux and macOS the installer renames the game's launcher rather than adding a separate executable, so you just launch the game normally and SMAPI comes along with it. No launch options needed.

## Back Up Your Saves!
Mods in Stardew Valley can and do write into your save file. A mod that adds items puts those items in your save, and removing that mod later can leave the save unable to load.

Back up this folder before you start.

```
C:\Users\<user>\AppData\Roaming\StardewValley\Saves
```

On Linux it's `~/.config/StardewValley/Saves` and on macOS it's `~/.config/StardewValley/Saves` as well.

**TIP** - SMAPI installs a bundled mod called **Save Backup** that automatically backs up all your saves once per day. It's genuinely one of the better reasons to use SMAPI even if you install nothing else.

## What Is SMAPI?
**SMAPI** (the Stardew Modding API) is a mod loader. It sits between Stardew Valley and your mods, gives them a way to hook into the game, and handles all the awkward parts like load order, version checks and error handling.

Practically speaking, it does three things you'll notice.

* It creates and reads a **`Mods`** folder in your game directory. That's where every mod goes.
* It opens a **console window** alongside the game listing what loaded and what went wrong.
* It catches mod errors so a broken mod prints a message instead of crashing your game.

Almost everything on Nexus Mods needs it. The exceptions are content-replacement packs that overwrite the game's own files directly, and those are rare now because Content Patcher (which needs SMAPI) does the same job better.

## Installing SMAPI
### Downloading SMAPI
Get SMAPI from [smapi.io](https://smapi.io/) or from its [Nexus Mods page](https://www.nexusmods.com/stardewvalley/mods/2400). Both are the same download, maintained by **Pathoschild**.

![SMAPI On Nexus Mods](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/nexus_smapi.png)

1. **Download through Vortex (mod manager)**: The orange **Vortex** button hands the file to the mod manager.
2. **Manual download**: **Manual** downloads the archive through your browser.

For this section we want the **Manual** download, because SMAPI has its own installer.

![The Free Download Option On Nexus Mods](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/nexus_smapi_download.png)

1. **Free downloads are slower, but free**: **Slow download** is throttled to around 1.5-3 MB/s with a short delay before it starts. SMAPI is about 40 MB so this takes seconds either way.

### Running The Installer
Extract the archive and open the folder inside.

![The SMAPI Installer Folder](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/smapi_installer_folder.png)

1. **Run this to install SMAPI**: `install on Windows.bat`. Linux and macOS users get their own script in the same folder.
2. **Manual install steps, if you need them**: `README.txt` documents the manual process. You almost certainly don't need it - the installer is the recommended route and the README says so itself.

Double-click the installer and it asks where your game is.

![SMAPI Asking Where The Game Is](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/smapi_install_path.png)

1. **SMAPI found the game**: It scans your drives and lists what it found. Type `1` and press enter, or pick `2` if you need to point it somewhere else.

Then it asks what you want to do.

![SMAPI Asking Install Or Uninstall](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/smapi_install_choice.png)

1. **Type 1 and press enter**: **Install SMAPI**. Option 2 removes it cleanly later if you ever want your game back to vanilla.

It takes a couple of seconds, and then tells you exactly what to do next.

![SMAPI Installed Successfully](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/smapi_installed.png)

1. **Copy this into your Steam launch options**: The full path to `StardewModdingAPI.exe` followed by `%command%`. Copy this line exactly - the next section covers where it goes.
2. **Or just run StardewModdingAPI.exe**: If you're not on Steam, that's all you need. Run that file in your game folder instead of the game.

Notice what it did along the way: **Creating mods directory** and **Adding bundled mods** - Console Commands and Save Backup. Those two folders showing up in `Mods` is normal and you should leave them there.

### Setting Up The Steam Launch Option
On Steam you *could* just run `StardewModdingAPI.exe` from the game folder, but then Steam doesn't know the game is running, so you lose achievements, playtime tracking and the overlay. The launch option fixes that.

Open your Steam library, right-click **Stardew Valley** and choose **Properties**.

![Opening Stardew Valley's Properties In Steam](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/steam_properties.png)

1. **Right-click the game and open Properties**: The **Properties** entry at the bottom of the context menu.

Then find **Launch Options** on the **General** tab.

![Setting The Launch Options In Steam](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/steam_launch_options.png)

1. **Paste the SMAPI path here, then %command%**: The line SMAPI's installer gave you, quotes and all.

It should look like this, with your own path.

```text
"G:\SteamLibrary\steamapps\common\Stardew Valley\StardewModdingAPI.exe" %command%
```

**WARNING** - The quotes matter, and so does `%command%`. Without the quotes Steam breaks the path at the space in "Stardew Valley", and without `%command%` Steam doesn't pass its own arguments through.

**TIP** - To play unmodded for a session, just clear the launch options box. Nothing is uninstalled, the game simply starts without SMAPI.

### Launching The Game
Hit **Play** in Steam and a console window opens alongside the game.

![The SMAPI Console](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/smapi_console.png)

1. **Every mod SMAPI loaded, with its version**: Here it's **Console Commands**, **Save Backup** and **Tractor Mod 4.24.4 by Pathoschild**. If a mod isn't in this list, it didn't load, and SMAPI will usually say why a few lines further down.

That console window is the single most useful thing about modding this game. Leave it open - errors, warnings and mod update notices all appear there, and it's the first place to look when something goes wrong.

**NOTE** - SMAPI also warns about software it knows can conflict, like overlays and monitoring tools. The message in the screenshot about MSI Afterburner is exactly that, and it's a warning rather than an error.

## Where To Download Mods
The main source is [Nexus Mods](https://www.nexusmods.com/stardewvalley), which has over 30,000 Stardew Valley mods.

Others worth knowing about are below.

* [CurseForge](https://www.curseforge.com/stardewvalley) - the second biggest, with its own desktop app. Covered [below](#installing-mods-through-the-curseforge-app).
* [ModDrop](https://www.moddrop.com/stardew-valley) - smaller, but some mods are exclusive to it.
* [Stardew Valley Forums](https://forums.stardewvalley.net/forums/mods.25/) - the official forum's mod board.
* [TMC](https://moddingcommunity.com/stardew-valley/mods) - us! We're still new.

**TIP** - Before installing anything, check it against the [SMAPI mod compatibility list](https://smapi.io/mods). It's community-maintained, it's searchable, and it will tell you in one line whether a mod works with your game version - which is faster than reading three pages of comments.

## The Mod We're Installing
[Tractor Mod](https://www.nexusmods.com/stardewvalley/mods/1401) by **Pathoschild** lets you buy a tractor garage from Robin, and then drive a tractor around your farm harvesting, watering, tilling and clearing debris in a wide radius. It is an enormous quality-of-life upgrade once your farm gets big.

It's a good example mod for three reasons: it's popular, it's actively maintained, and its Nexus page shows off a quirk that confuses a lot of people.

![Tractor Mod On Nexus Mods](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/nexus_tractor.png)

1. **Only a Manual button up here**: There's no orange **Vortex** button in the header. That does **not** mean the mod is manual-only.
2. **The Files tab has the Vortex button**: Switch to **FILES** and each individual file gets its own mod manager button.

Here's the Files tab.

![The Files Tab On Nexus Mods](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/nexus_tractor_files.png)

1. **The SMAPI version this file needs**: "Requires SMAPI 4.1.10 or later." Always worth a glance - a mod needing a newer SMAPI than you have is one of the two or three most common reasons a mod doesn't load.
2. **Mod manager download (Vortex)**: Hands the file to Vortex.
3. **Manual download**: Downloads the `.zip` through your browser.

Note the second file in the list, **Tractor Mod 4.24.3**, marked "For players on Android phones only". Grabbing an older file because it was higher up the page is an easy mistake to make. Read the notes.

## Installing Mods Manually
This is the normal way to install Stardew Valley mods, and it's genuinely a two-step process.

### Downloading The Mod
Use the **Manual download** button on the Files tab. You'll get a `.zip`.

### Extracting And Copying
Extract the archive with [7-Zip](https://www.7-zip.org/) and look at what came out.

![The Extracted Mod Folder](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/manual_extracted.png)

1. **This folder is what goes into Mods**: A single folder named `TractorMod`, containing the mod's `manifest.json` and its files.

Copy that folder into your game's `Mods` folder.

```
C:\Program Files (x86)\Steam\steamapps\common\Stardew Valley\Mods
```

![The Mods Folder](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/mods_folder.png)

1. **SMAPI's own bundled mods**: `ConsoleCommands` and `SaveBackup`, installed by SMAPI. Leave them alone.
2. **One folder per mod**: `TractorMod`. That's the whole installation.

So the final structure is this.

```text
Stardew Valley\Mods\TractorMod\manifest.json
Stardew Valley\Mods\TractorMod\...
```

**WARNING** - Don't nest the folder. `Mods\TractorMod\TractorMod\manifest.json` will not load, and it's the most common manual-install mistake by a distance. SMAPI looks for `manifest.json` one or two levels deep, and it will tell you in the console if it can't find one - but it's easier to just get it right.

**TIP** - You can also create subfolders inside `Mods` to organise things - `Mods\Farming\TractorMod` works fine. SMAPI searches recursively.

For reference, this is what your game folder looks like after SMAPI is installed.

![The Stardew Valley Game Folder](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/game_folder.png)

1. **StardewModdingAPI.exe - launch this**: Sitting right next to `Stardew Valley.exe`. This is what your Steam launch option points at.

## Installing Mods Through Vortex
[Vortex](https://www.nexusmods.com/vortex) is the official mod manager from Nexus Mods. It's more machinery than Stardew Valley strictly needs, but it's genuinely useful once you're running twenty-odd mods and want update checks and one-click installs.

For a full walkthrough of Vortex, see our dedicated [**How to Use Vortex & The Basics**](https://moddingcommunity.com/blog/how-to-use-vortex-and-basics) guide. The sections below cover the Stardew Valley specific parts.

### Managing Stardew Valley In Vortex
Vortex won't touch a game until you tell it to manage that game.

![Managing Stardew Valley In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_manage.png)

1. **Search for the game**: Open **Games** in the left sidebar and type `stardew` into the search bar.
2. **Hover the tile and click Manage**: Vortex scans for the install and adds Stardew Valley to the left rail.

If Vortex can't find your install, click the **three dots (⋮)** in the corner of the tile, choose **Manually Set Location**, and point it at the folder containing `Stardew Valley.exe`.

### Letting Vortex Install SMAPI
Vortex knows Stardew Valley needs SMAPI and will tell you if it isn't there.

![Vortex's SMAPI Notification](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_smapi_notification.png)

1. **Get SMAPI** takes you straight to the download.

If you already installed SMAPI with its own installer, this notification just won't appear. If you'd rather Vortex handled it, click the button and let it install SMAPI like any other mod.

![Vortex's Download Dialog](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_download_dialog.png)

1. **Free accounts download one at a time**: **Download manually** opens the Nexus page for the file. Premium accounts get **Auto-download all**, which fetches everything without the page visits.

Once it's in, SMAPI shows up on the **Mods** page like anything else.

![SMAPI Installed In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_smapi_installed.png)

1. **SMAPI installed and enabled**: Categorised under **Modding Tools**.
2. **Compatibility check**: Vortex checks mods against a compatibility database for this game and flags anything known to be broken. A green tick is good, the info icon means there's something to read.

**NOTE** - Installing SMAPI through Vortex does **not** set up the Steam launch option. That part is still on you, and it's covered in [Setting Up The Steam Launch Option](#setting-up-the-steam-launch-option) above.

### Installing A Mod
Head to the mod page, open the **FILES** tab, and use **Mod manager download**. Your browser will ask for permission to open Vortex - accept it, and tick **Always allow** if you'd rather not be asked every time.

Vortex downloads it, installs it, and drops the folder into your `Mods` directory for you.

### The Mods Page
Everything you've installed lives here.

![The Mods Page In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_mods_overview.png)

1. **Enable, disable or uninstall**: The **Status** drop-down for each mod.
2. **Remove, or open the actions menu**: **Remove** uninstalls the mod, and the arrow beside it opens the full actions menu.

The status drop-down has three options.

![The Status Drop-Down In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_mods_status.png)

1. **The three states a mod can be in**: **Enabled** means the mod folder is in your `Mods` directory. **Disabled** keeps the mod in Vortex but pulls the folder back out. **Uninstalled** removes the files but keeps the downloaded archive so you can reinstall without downloading again.

The actions menu covers everything else.

![The Mod Actions Menu In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_mods_actions.png)

1. **Everything else you can do to a mod**: The options are as follows.
    * **Reinstall** - runs the installer again.
    * **Remove related** - removes the mod and anything tied to it.
    * **Check for Updates** - asks Nexus Mods for a newer version.
    * **Manage File Conflicts** - decides which mod wins when two write the same file.
    * **Open in File Manager** - opens the mod's staging folder.
    * **Open Archive** - opens the downloaded archive.
    * **Install Recommendations** - installs mods the author recommends alongside this one.
    * **Refresh Content** - re-reads the mod's files from disk.
    * **Create Report** - generates a report, useful when asking for help.
    * **Open on Nexus Mods** - opens the mod page in your browser.

**NOTE** - Stardew Valley has no plugins and no load order, so Vortex's sidebar here is shorter than it is for Bethesda games. There's no **Plugins** page because there's nothing to order.

### Launching Through Vortex
Vortex's **Play** button launches the game with SMAPI.

![The Play Button In Vortex](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/vortex_play.png)

1. **Play launches the game through SMAPI**: Vortex picks up `StardewModdingAPI.exe` automatically once SMAPI is installed.

## Installing Mods Through The CurseForge App
[CurseForge](https://www.curseforge.com/download/app) is the other big mod host, and its desktop app supports Stardew Valley. If you already use it for Minecraft, this will feel familiar.

![Browsing Stardew Valley Mods In CurseForge](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/curseforge_browse.png)

1. **Browse lists every Stardew mod**: Around 1,800 projects, sortable by downloads, category and game version.
2. **Install straight into Mods**: One click. CurseForge downloads the mod and extracts it into your `Mods` folder for you.
3. **SMAPI is here too**: SMAPI is the top result and can be installed from here as well.

Your installed mods show under **My Mods**.

![My Mods In CurseForge](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/raw/main/images/curseforge_mymods.png)

1. **Your installed mods**: With the installed version, the game version it targets and the author. **Update all** at the top updates everything in one go.

CurseForge is arguably the least fuss of the three methods for this game - it's one click per mod and it handles updates - but its Stardew library is smaller than Nexus Mods, so you'll likely end up mixing methods.

**WARNING** - Don't manage the same mod in two places. If Vortex and CurseForge both think they own `Mods\TractorMod`, you'll end up with duplicates or a mod that reappears after you remove it. Pick one manager per mod, or install by hand.

**TIP** - For a full walkthrough of the CurseForge app, see our [**How to Use the CurseForge App & The Basics**](https://moddingcommunity.com/blog/how-to-use-curseforge-app-and-basics) guide.

## Checking If Your Mods Loaded
Launch the game and read the SMAPI console. Your mod should be in the **Loaded N mods** list with its name, version and author.

For Tractor Mod specifically, go to **Robin's carpenter shop** and you'll find a new **Tractor Garage** for sale at 150,000g (plus an Iron Bar, an Iridium Bar and a Battery Pack). Build it, and the tractor is inside.

If the mod isn't in the list, work through the following.

* Is the folder structure right? It should be `Mods\ModName\manifest.json`, not `Mods\ModName\ModName\manifest.json`.
* Did the console print a **skipped mod** warning? SMAPI names the mod and the reason.
* Is your SMAPI new enough? The mod page states the minimum version.
* Did you launch through SMAPI rather than the game directly?
* Is the mod listed as broken on the [compatibility list](https://smapi.io/mods)?

## Updating & Removing Mods
Updating is the same process as installing - download the new version and replace the folder.

1. **Back up the mod's `config.json`** if you've customised it. Most mods keep your settings when you overwrite the folder, but not all of them.
2. **Delete the old folder** rather than pasting over it. Leftover files from an old version are a real source of odd behaviour.
3. **Copy the new folder in.**

Removing a mod is just deleting its folder from `Mods`.

**WARNING** - Removing a mod that added items or buildings to your save can break that save. If a mod's page has uninstall instructions, follow them - usually something like selling everything the mod added before you remove it.

**TIP** - SMAPI checks for mod updates on startup and prints them in the console, so you'll be told when something is out of date without having to check manually.

## Other Useful Mods
A few mods are worth installing early because so many other mods depend on them, or because they make everything else easier.

* **[Content Patcher](https://www.nexusmods.com/stardewvalley/mods/1915)** - lets mods change the game's images, maps and data without touching game files. A huge share of Stardew mods are Content Patcher packs, so you'll end up with it whether you plan to or not.
* **[Generic Mod Config Menu](https://www.nexusmods.com/stardewvalley/mods/5098)** - adds an in-game settings menu for any mod that supports it, which is most of them. Without it, configuring mods means editing `config.json` files in Notepad.
* **[Lookup Anything](https://www.nexusmods.com/stardewvalley/mods/541)** - press a key over anything in the game to see its details. Not a dependency, just extremely useful.
* **[SpaceCore](https://www.nexusmods.com/stardewvalley/mods/1348)** - a framework a lot of larger content mods build on.

## Troubleshooting
- **No console window appears.** You launched the game rather than SMAPI. Check your Steam launch options, or run `StardewModdingAPI.exe` directly.
- **SMAPI says a mod was skipped.** Read the line - it names the reason, usually a missing dependency or an outdated mod.
- **The mod isn't listed at all.** The folder structure is wrong, or you put it somewhere other than `Mods`.
- **SMAPI says it can't find the game.** Point the installer at the folder manually with option 2.
- **The game crashes on startup after an update.** SMAPI is older than your game version. Download the current SMAPI and run the installer again.
- **A mod worked yesterday and doesn't today.** The game auto-updated. Same fix - update SMAPI, then check the mod on the [compatibility list](https://smapi.io/mods).
- **My save won't load.** A mod that wrote into the save has been removed. Put it back, load the save, and follow the mod's uninstall instructions properly.
- **Achievements stopped working.** You're launching SMAPI outside Steam. Use the launch option instead.

## Notes
### Multiplayer
Multiplayer works with mods, with one rule: **everyone needs the same mods**. SMAPI checks this when you connect and warns about mismatches.

Some mods are client-side only (UI tweaks, visual changes) and don't need to match. Anything that changes gameplay, items or maps does. Mod pages usually say which they are, and SMAPI will tell you in the console when a connecting player is missing something.

### Mod Config Files
Most SMAPI mods create a `config.json` inside their own folder the first time you run them. That's where per-mod settings live - keybinds, toggles, balance numbers.

You can edit those files in Notepad, but [Generic Mod Config Menu](https://www.nexusmods.com/stardewvalley/mods/5098) gives you an in-game settings screen for the same options, which is a lot less error-prone than hand-editing JSON.

**NOTE** - A `config.json` with a syntax error stops the mod loading. If you edit one by hand and the mod disappears from SMAPI's list, that's almost certainly why - delete the file and the mod will regenerate it with defaults.

## See Also!
* [SMAPI](https://smapi.io/)
* [SMAPI mod compatibility list](https://smapi.io/mods)
* [Nexus Mods - Stardew Valley](https://www.nexusmods.com/stardewvalley)
* [Tractor Mod](https://www.nexusmods.com/stardewvalley/mods/1401)
* [CurseForge - Stardew Valley](https://www.curseforge.com/stardewvalley)
* [Stardew Valley Modding Wiki](https://stardewvalleywiki.com/Modding:Index)
* [How to Use Vortex & The Basics](https://moddingcommunity.com/blog/how-to-use-vortex-and-basics)
* [How to Use the CurseForge App & The Basics](https://moddingcommunity.com/blog/how-to-use-curseforge-app-and-basics)
* [ProtonDB - Stardew Valley](https://www.protondb.com/app/413150) (for Linux users)
* [r/SMAPI](https://www.reddit.com/r/SMAPI/)

## Conclusion
That's it! Stardew Valley is about as painless as modding gets once SMAPI is in place, and after that adding a mod really is just copying a folder.

The short version - install **SMAPI** first, set the **Steam launch option** so you keep achievements, drop each mod as **one folder** into `Mods`, and read the **SMAPI console** when something doesn't work because it will usually tell you exactly what's wrong.

Guides we create are always open to edits and improvements, so if you have any suggestions or notice any issues, feel free to contribute by creating a [pull request](https://github.com/modcommunity/how-to-install-mods-in-stardew-valley-for-pc/pulls) on our GitHub repository!

Please join our [Discord server](https://discord.moddingcommunity.com) if you have any questions or need help with anything related to modding or our guides!
