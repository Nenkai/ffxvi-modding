---
icon: material/folder-plus
---

# Creating Mods

## Creating Mods for the FFXVI Mod Loader

Once you have modded assets you'd like to mod into the game:

1. First, follow the [Reloaded II Creating Mods tutorial](https://reloaded-project.github.io/Reloaded-II/CreatingMods/) for general information about creating a mod for Reloaded-II.
2. Set the `FINAL FANTASY XVI Mod Loader as a dependency`. Reloaded-II will prompt you to set mod dependencies when creating the mod.
3. Your mod's assets must be contained within the `FFXVI/data` folder. Example:

!!! example
    ```{ .sh .no-copy }
    .
    ├─ ff16.<category>.<mymodname>/
    │  └─ FFXVI/
    │     └─ data/
    │        └─ 0007/ # <- Your pack must match the original pack name. 0007 is an example.
    │           │
    │           ├─ .path  # IMPORTANT: This file is needed if there is one present.
    │           └─ <files to mod for this pack>
    │
    ├─ ModConfig.json
    └─ ...
    ```

!!! info "Template/Sample Mod"
    :material-download: An example mod can be found [here](https://github.com/Nenkai/ff16.utility.modloader/releases/download/1.0.1/ff16.template.helloworld.zip). This changes the bottom-left text of the main title screen to add "Hello World".

If you have successfully gotten your mod to work, congratulations!

---

## Creating Mods for Manual Installation

Refer to [Modding Manually](./installing_mods.md#modding-manually) on the Installing Mods page.

---

## Publishing Mods & Guidelines

[Nexus Mods](https://www.nexusmods.com/finalfantasy16/mods/) is the primary website to publish mods.