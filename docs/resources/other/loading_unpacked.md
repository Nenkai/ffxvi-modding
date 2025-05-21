---
icon: material/package-variant
---

# :material-package-variant: Loading Unpacked

It is possible to run the game unpacked.

1. Unpack all game contents into **any of the following** folders in the game's directory by using FF16Tools's `unpack-all-packs` command:
    * `resources_win/release/master` 
    * `resources/release/master`

2. Ensure to rename the `data` folder to anything else, so that the game doesn't see it i.e `_data`.

The game should then try and load files from these folders. If unsure, use [Procmon](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) to see what the game is trying to load.

!!! warning "Nested Packs"
    Nested packs must remain packed. There is no way to also load these unpacked.