---
icon: material/magic-staff
---

# :magic_wand: Magic/Depend Resource

Magic files are pointed to from the `model` table.

Before loading the `.magic` file, a `.dep` file is loaded from the pack `system/game/magic/depend_resource_info.pac`. 

## `.dep`

Registers all entities/dependencies related for a `.magic` file.

[010 Editor Template here](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_dep_MagicDependResource.bt).

## `.magic`

Magic files contain spell, or dynamic projectile definitions that can be created by characters/enemies (BNpcs). Each BNpc has their own file which is different and two spells can have the same Id and yet be different, as long as they're contained in two different characters' files.

These files are at `chara/<id>/magic/<id>.magic` (You will need to extract `chara/<id>/pack/<id>.pac`).

A magic file defines magic ids, which are instantiated through [chara timelines](../../tutorials/timelines/chara_timelines.md).

One magic 'entry' may contain groups of operations, which are uniquely identified by their own Id. These groups contain operations, which declares a magic's behavior, such as initialize a linear projectile, a VFX ([vfxb id](vatb.md)), the hitbox, and a lot more.

These operations contain properties. These properties merely just set up how an operation behaves. (Under the hood, all they really do is set an operation's internal field to a value).

Operations may have properties that point to other groups by Id - they are essentially callbacks.

[010 Editor Template here](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_magic.bt).

!!! tip
    You can edit magic files at runtime using [FaithFramework](https://www.nexusmods.com/finalfantasy16/mods/138) - Head to the resource manager and look for magic files.

---

For a quick example, Magic 3 (in `c1001.magic`) is Clive's Normal (non charged) shot.

It declares 4 groups:

* `4337` - Used to initialize the magic with operation 51 (you'll see this one a lot), which [Eid](../ids/eid.md) to use for the current actor, and which target to use.
* `4338` - Creates a projectile.
* `4340` - Callback group for when the target was hit.
* `4354` - Callback group for when the projectile 'expired' - it hit nobody.