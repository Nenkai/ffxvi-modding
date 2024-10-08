---
icon: material/folder-download
---

# Mod Manager

The Reloaded II mod manager combined with the FINAL FANTASY XVI Mod Loader is the primary way to manage mods for FFXVI. 

It quickly handles what would normally be a multi-step process with `FF16.Tools` for all managed mods.

---

## Requirements

* :material-github: [Reloaded-II Mod Manager](https://github.com/Reloaded-Project/Reloaded-II/releases)
* :simple-nexusmods: [ff16.utility.modloader (Mod Loader)](https://www.nexusmods.com/finalfantasy16/mods/3) - :material-github: [Github Mirror](https://github.com/Nenkai/ff16.utility.modloader/releases/)
* :simple-7zip: [7-Zip](https://www.7-zip.org/) to extract Reloaded-II (if not using the setup)

---

## Video Tutorial 

<video controls>
    <source src="../reloadedii-mods-install.mp4" type="video/mp4">
</video>

## Text Tutorial

### Setting up Reloaded-II

1. Download Reloaded-II's `Release.zip`, or `Setup.exe`.
2. Extract `Release.zip` to its own folder or run the `Setup.exe` and install it.
3. Open `Reloaded-II.exe`.
4. Press the `+` Icon to add a game and select `ffxvi.exe`.
5. Drag & Drop `ff16.utility.modloader.7z` to Reloaded-II. You may need to restart Reloaded-II to be able to drag-drop.
6. In Reloaded-II make sure to tick on the checkbox next to `FINAL FANTASY XVI / 16 Mod Loader` to enable it.

!!! info

    For more information if needed, refer to the Reloaded II [Quick Start Guide](https://reloaded-project.github.io/Reloaded-II/QuickStart/).

---

### Installing Mods

1. Download a mod. You can find mods on sites like Nexus Mods and GameBanana. Make sure that they are compatible with Reloaded-II.
2. Same process, drag & drop.
3. Press `Launch Application` to launch the game and install the mods.

---

## Removing Mods

To remove mods, you can either:

* Disable all mods in Reloaded-II **except** the Mod Loader, and boot up once, or
* Delete any `.diff` files in the game's `data/` folder.

---

## Modding Manually

!!! warning

    If you intend to publish mods, you should create mods for Reloaded-II instead of modding manually. Otherwise pack files may conflict.

If you'd like to mod contents manually, you can do so using [FF16Tools](https://github.com/Nenkai/FF16Tools).

You may choose to rebuild a `.pac` entirely, or **preferably** you can use `.diff.pac` files.

When packing an extracted folder, the output pack file should have `.diff` in its name. The game will load this file.

So if your files came from `0000.pac`, the new pac file should be `0000.diff.pac`. 

Then run the following command:
``` markdown title="Command"
FF16Tools.exe pack -i <path to folder> 
```