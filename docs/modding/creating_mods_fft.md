---
icon: material/folder-plus
---

# Creating Mods

## Creating Mods for the FFTIVC Mod Loader

First, extract the game files using FF16Tools. Refer to [this page](https://ffhacktics.com/wiki/FFT/TIC/PAC_Files) for more information about files.

Once you have modded assets you'd like to mod into the game:

1. First, follow the [Reloaded II Creating Mods tutorial](https://reloaded-project.github.io/Reloaded-II/CreatingMods/) for general information about creating a mod for Reloaded-II.
2. Set the `FINAL FANTASY TACTICS - The Ivalice Chronicles Mod Loader` as a dependency. Reloaded-II will prompt you to set mod dependencies when creating the mod.
3. Make sure you target the Enhanced, or Classic versions (or both).
4. Your mod's assets must be contained within the `FFTIVC/data/<game mode>` folder. Example:

!!! example "Example Mod Folder Structure"

    **Click the :material-plus-circle:'s below for more information.**
     ```{ .sh .no-copy .annotate }
     .
     ├─ fftivc.<category>.<mymodname>/
     │  └─ FFTIVC/
     │     ├─ enhanced/ # (1)!
     │     │   ├─ nxd/ui.en.nxd
     │     │   ├─ ui/ffto/title/texture/ui_title_top_bg_uitx.tex
     │     │   ...
     │     │
     │     ├─ classic/ # (2)! Classic Version.
     │     └─ combined/ # (3)!
     │
     ├─ ModConfig.json
     └─ ...
     ```

    1.  Files in this folder will apply to the Enhanced Version.

    2.  Files in this folder will apply to the Classic Version.

    3.  Files in this folder will go in both enhanced and classic.

!!! info "Template/Sample Mod"
    :material-download: A sample mod can be found [here](https://github.com/Nenkai/fftivc.utility.modloader/releases/download/1.0.0/fftivc.test.samplemod.zip). This does various test changes to the title menus for both versions.

If you have successfully gotten your mod to work, congratulations!

## Final Fantasy Hacktics Discord

For more tactics related modding, refer to the Final Fantasy Hacktics Community [website](https://ffhacktics.com/) and [discord](https://discord.gg/xpXa8VEV2k).