---
icon: material/map
---

# :material-map: Game Maps

Game Maps are defined in the [`gamemap`](../tutorials/nex/tables.md) Nex table and will point to files located in the `map` folder.

The main file is file is always the `.mpb`, which presumably stands for **M**a**p** **B**inary.

`gamemap` may also point to:

* `layoutsetting`, which is used to control which files aside from the `.mpb` file is loaded.
* `mapdirector`, which controls some behavior on the map (battles and more).
* (and more)

## Map Binary

The `.mpb` contains all the entities linked to a map file. More precisely, it holds a basic tree of all entities present in a map.

* List of `GroupList`
    * List of `Group`
      * List of `Entity`
        * `Entity` (Model)
        * `Entity` (StageSet (aka prefab))
        * `Entity` (BNpc)
        * `Entity` (Trigger)
        * and more

All entities that point to files are done so by path references. For instance, a Model entity will usually point to a model file in the `env` folder i.e `env/bgparts/common/accessory/g01/model/b0_acce_g01_barrel02.mdl`.

Every `Group` and `Entity` are identified by a unique Id, also known as `LayoutInstances` referenced across many Nex tables.

Furthermore, each `Group` and `Entity` may point to a `placement` row in Nex, which can control whether the entity is active depending on `usersituation` flags specified in `placement`.


## Entities

All entities have a **Position**, **Rotation** and **Scale** on the map, aswell as additional data depending on the type of entity.

More information in the [010 Editor template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_mpb_MapBinary.bt)