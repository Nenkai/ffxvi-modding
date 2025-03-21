---
icon: material/microsoft-excel
---

# :material-microsoft-excel: Nex (NXD) Conversion

Nex files are pretty much the database of the game. Originally in Excel form, SQEX converts them into a binary format named `.nxd` (sister of FF14's `.exd`).

!!! tip

    * Some tables are described [here](tables.md) - **highly recommended to read, especially the union bit**
    * Refer to the [table layouts here](https://github.com/Nenkai/FF16Tools/tree/master/FF16Tools.Files/Nex/Layouts) for the column value types. Note: this has been mapped mostly manually. **Please contribute!** Many columns are still unknown. **There may be comments about some columns in each layout; recommended to read**

## Requirements

* :material-github: [FF16Tools](https://github.com/Nenkai/FF16Tools) - **It is recommended to always use the latest version as column names will be renamed.**
* :simple-sqlite: [SQLiteStudio](https://sqlitestudio.pl/)

### Converting to SQLite

Using `FF16Tools.CLI`, run the following command:

```
FF16Tools.CLI nxd-to-sqlite -i <path to directory with nxd>
```

This will convert all the `.nxd`'s in a directory to a SQLite database you can open with **SQLiteStudio**.

!!! tip

    More information is available in the [Tables](tables.md) page.


---

## Editing

??? tip "Method 1: Live Nex Editor"

    You can use the [Live Nex Editor](https://www.nexusmods.com/finalfantasy16/mods/289) to edit nex rows while the game is running.

    !!! note

        If you need to add/remove rows, or edit strings/resize arrays, you will need to refer to **Method 2** instead.

??? tip "Method 2: Converting back to Nex"

    ```
    FF16Tools.CLI sqlite-to-nxd -i <path to sqlite file>
    ```

    !!! tip

        You can provide the `-t` argument to only convert certain tables. for instance, `-t equipitem command` will only save `equipitem.nxd` and `command.nxd`.

!!! note

    * Always check the [Changelog](https://github.com/Nenkai/FF16Tools/blob/master/NEX_CHANGELOG.md) for updated table column names.
    * Nex can contain nested data, therefore arrays and other structs are converted to json strings.
    * Nex can contain row sets that don't actually contain any rows. This information is lost between SQLite conversion, but should *hopefully* not matter.
    * You may need to edit `root.nxl` to reflect the number of rows (if you've added/removed any).