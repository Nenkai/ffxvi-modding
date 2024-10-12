---
icon: material/folder-plus
---

# Creating Mods

## Creating Mods for the FFXVI Mod Loader

Once you have modded assets you'd like to mod into the game:

1. First, follow the [Reloaded II Creating Mods tutorial](https://reloaded-project.github.io/Reloaded-II/CreatingMods/) for general information about creating a mod for Reloaded-II.
2. Set the `FINAL FANTASY XVI Mod Loader as a dependency`. Reloaded-II will prompt you to set mod dependencies when creating the mod.
3. Your mod's assets must be contained within the `FFXVI/data` folder. Example:

!!! example "Example (Mod Loader >= 1.1.0)"

    **The mod loader will automatically determine in which pack your game files should be according to [this list](../resources/asset_paths.md).** (pack-named folders is still supported for compatibility purposes).

    ```{ .sh .no-copy .annotate }
    .
    ├─ ff16.<category>.<mymodname>/
    │  └─ FFXVI/
    │     └─ data/
    │        ├─ ui/gameflow/title/title01.uib # (1)!
    |        ├─ nxd/en/equipitem.nxd # (2)!
    │        ...
    │
    ├─ ModConfig.json
    └─ ...
    ```

    1.  This will go in pack `0028`.

    2.  A sub-folder with a locale name will appropriately put it in the correct locale pack. `nxd/en/equipitem.nxd` will translate to pack `0007.en` and put `nxd/equipitem.nxd` inside it.

    Also, any changes you make to [Nex](../tutorials/nex/nxd_editing.md) tables won't replace files altogether, but only cell changes you've made to increase compatibility. **This also means that you should only edit cells you actually need to edit to avoid potential conflicts.**

??? example "Example (Mod Loader < 1.1.0)"
    ```{ .sh .no-copy }
    .
    ├─ ff16.<category>.<mymodname>/
    │  └─ FFXVI/
    │     └─ data/
    │        └─ 0007/ # <- Your pack must match the original pack name. 0007 is an example.
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