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

Contain a set of magic spells (basically blueprints that can be instantiated into spells) that can be used by characters. Each character has their own file which is different and two spells can have the same Id and yet be different, as long as they're contained in two different characters' files.

It seems like these spell "blueprints" are divided into lists, which are then divided into distinct operations each containing a number of properties. Every property has a type and data (usually 4byte int or float) that represents different things based on the type.
Basically properties just sets up an operation's parameter.

The current guess is that magic spells are instances of these spell objects / blueprints, and the magic file contains data for spell size, velocity, direction, VFXAudio, AttackParam etc.

Instances of spells are basically any attack that's not connected to any BNpc, which makes them unrelated to the character's collision files.
They're like volatile npcs with their own collision, movement.

[010 Editor Template here](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_magic.bt).