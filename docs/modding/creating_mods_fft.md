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
     │     └─ data
     │        ├─ enhanced/ # (1)!
     │        │   ├─ fftpack/... # (2)!
     │        │   ├─ nxd/ui.en.nxd
     │        │   ├─ system/ffto/g2d/tex_<fileIndex>.bin # (3)!
     │        │   ├─ ui/ffto/title/texture/ui_title_top_bg_uitx.tex
     │        │   ...
     │        │
     │        ├─ classic/ # (4)!
     │        └─ combined/ # (5)!
     │
     ├─ ModConfig.json
     └─ ...
     ```

    1.  Files in this folder will apply to the Enhanced Version.

    2.  Refer to the section below for modding FFTPack files.

    3. Overrides a certain file in `g2d.dat`. 
    
        **Must follow the `tex_<fileIndex>.bin` scheme.**
    
        The `.bin` extension is not a requirement and can be anything else.

        More info in another section below.

    4.  Files in this folder will apply to the Classic Version.

    5.  Files in this folder will go in both enhanced and classic.

!!! info "Template/Sample Mod"
    :material-download: A sample mod can be found [here](https://github.com/Nenkai/fftivc.utility.modloader/releases/download/1.0.0/fftivc.test.samplemod.zip). This does various test changes to the title menus for both versions.

If you have successfully gotten your mod to work, congratulations!

## G2D (Graphics2D) Texture Modding

Use [this tool](https://ffhacktics.com/smf/index.php?topic=13375.0) to extract `g2d.dat`.

Once edited, files belong to `system/ffto/g2d/tex_<fileIndex>.bin`.

You can also use `system/ffto/g2d.<en/jp>` in the case of locale g2ds in classic, though it does not seem that classic uses it at all.

## FFTPack modding

**NOTE: Requires loader version 1.2.0 or later**.

The game (enhanced at least) stores `fftpack.bin` in `system/ffto` aswell as an extracted version in the `fftpack` folder. Originally, some files may still be pulled out of `fftpack.bin`.

The loader allows bypassing this behavior so that a file inserted in `fftpack/` will always be loaded off your mod folder (aswell as being inserted into the modded pack).

!!! tip
    
    The game itself overrides `fftpack/event_test_evt` to load from the `script/` folder instead. Use this folder instead to mod scripts!

---

## Final Fantasy Hacktics Discord

For more tactics related modding, refer to the Final Fantasy Hacktics Community [website](https://ffhacktics.com/) and [discord](https://discord.gg/DCRyr9DYFT).