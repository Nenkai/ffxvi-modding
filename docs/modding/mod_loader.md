---
icon: material/format-list-checkbox
---

# :material-format-list-checkbox: Mod Loader Internals

!!! note
    This applies to mod loader version `1.1.0`.

## Main Process

The internal mod loader process is documented here.

1. When launching, the mod loader will immediately remove any `.diff` [pack](../resources/formats/pac.md) files present in the game's `data` directory. `.diff.pac` files essentially extend the base content with extra/modded contents. Cleaning it first means starting from a fresh state.
3. Every mod loaded by Reloaded-II which has a `FFXVI` folder will be picked up by the loader and keep track of every file (and accordingly translate them to the proper pack [according to this list](../resources/asset_paths.md)).
    * Support for folders named after packs is still supported (pre-1.1.0 behavior).
    * Nex tables (`.nxd`) changes from original to modded will be specifically recorded to allow more mods to be compatible if they edit the same table.
    * When mod files conflict, the last loaded one has priority.
3. The mod loader will inject its own edited files for the main menu mod information (if enabled).
4. Once Reloaded-II has alerted the mod loader that all mods have been loaded, the mod loader will merge all nex changes, and every other files provided for each pack by mods. The mod loader will begin to build each pack with [FF16Tools](https://github.com/Nenkai/FF16Tools/) and save them as `.diff.pac` files in the game's `data` folder.

Which means, file mods will persist when booting without Reloaded-II. However, Reloaded-II can also consist of *code-based* mods, so it is always recommended to boot through it.
