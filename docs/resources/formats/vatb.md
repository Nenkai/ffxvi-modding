---
icon: material/cast-audio-variant
---

# :material-cast-audio-variant: Vatb (VFX Audio Table Binary)

Vatb files contain a simple VFX/Audio path pair table. They essentially link one unique Id to a VFX and audio file to play.

These are pointed from `VFXAudioId` columns in the [Nex](../../tutorials/nex/nxd_editing.md) tables. Then, the game simply searches through all current registered vatb files, and all their entries, for an entry which its Id matches.

* [FF16Tools](https://github.com/Nenkai/FF16Tools/) is capable of converting them from and to json.
* [010 Editor Template here](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_vatb_VFXAudioTable.bt).
