---
icon: material/export
---

# File Extraction

## :material-folder-text: Game Files

!!! tip
    The game folder can be found under `<Steam Folder>\steamapps\common\FINAL FANTASY XVI`.

You should be able to find the following files/folders:

* `data/` - This is where the game data resides. Data is split between packs which correspond to different folders in the game.

---

## :material-folder-move: Extracting Files

### Requirements

* :simple-dotnet: [.NET 8.0](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
* :material-github: [FF16Tools](https://github.com/Nenkai/FF16Tools/releases)

---

### Extracting all files

Open a command prompt in the folder where `FF16Tools.CLI.exe` is, and then run the following command:

``` markdown title="Example Command - Extract all files"
FF16Tools.CLI.exe unpack-all -i <path to .pac file>
```

!!! note

    Replace `<path to .pac file>` with the path to an actual `.pac` file, (surrounded by double-quotes `"` if it contains spaces).

It may take some time to extract all files depending on the size.