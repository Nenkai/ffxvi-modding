---
icon: material/format-list-checkbox
---

# :material-format-list-checkbox: Mod Loader Internals

## Main Process

The internal mod loader process is documented here.

1. When launching, the mod loader will immediately remove any `.diff` [pack](../resources/formats/pac.md) files present in the game's `data` directory. `.diff.pac` files essentially extend the base content with extra/modded contents. Cleaning it first means starting from a fresh state.
2. Every mod loaded by Reloaded-II which has a `FFXVI` folder will be picked up by the loader and keep track of every file per-pack.
    * When mod files conflict, the last loaded one has priority.
3. Once Reloaded-II has alerted the mod loader that all mods have been loaded, the mod loader will merge every files provided for each pack by mods. The mod loader will begin to build each pack with [FF16Tools](https://github.com/Nenkai/FF16Tools/) and save them as `.diff.pac` files in the game's `data` folder.

Which means, file mods will persist when booting without Reloaded-II. However, Reloaded-II can also consist of *code-based* mods, so it is always recommended to boot through it.

## Implementation Caveats

All packs are basically just a mounted file-system. In theory *any* pack can include *any* folder/file in the game. 

At first the idea of not having folders per pack was obvious, but one problem is that localization works with localization-specific packs. There is no clear way to detect how to build localized contents without having pack specific folders.