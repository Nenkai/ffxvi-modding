---
icon: material/file-find
---

# :material-file-find: File Formats

## File System

* [`.pac`](pac.md) - DirectStorage Pack - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_pac_PACK.bt)

## Tables
* [`.nxd`](nxd.md) - Next ExcelDB Table - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_nxd_NXDF.bt)
* `root.nxl` - Table definitions

## Map/Levels

* `.mpb` - Map Binary (main file, loading all other map files) - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_mpb_MapBinary.bt)
* `.vatb` - VFX Audio Table Binary - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_vatb_VFXAudioTable.bt)
* `.ssb` - Stage Set Binary
* `.tnb` - Tanebi (??)
* `.vglb`
* `.veb`
* `.epb`
* `.mgb`
* `.emcb`
* `.sndenv` - Sound Environment
* `.sndmap` - Sound Map
* `.gid`
* `.gwb`
* `.tera` - Map Terrain Binarry
* `.aml` - Map Timeline

## Character
* `.tlb` - Character Move/Attack/Action Timelines - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_tlb_FileCharaTimeLine.bt)

## Models/Textures

* `.mdl` - Model - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_mdl_Model.bt)
* `.tec` - Shaders - [010 Editor Template](https://github.com/KillzXGaming/FF16-010-Templates/blob/main/TEC.bt)
* `.tex`/`.gtex` - Textures - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_tex_Texture.bt)
* `.vfxb` - Visual Effect Binary - [010 Editor Template](https://github.com/AlexPlaceres/FF16Templates/blob/main/Incomplete/vfxb.bt)
* `.panb`
* `.mtl` - Material - [010 Editor Template](https://github.com/KillzXGaming/FF16-010-Templates/blob/main/MTL.bt)
* `.spd8` - Speedtree
* `.gset`
* `.shb` - Shader Binary, also tec shaders
* `.srope` - Spline Rope

* `.anmb` - Havok Animation Binary
* `.skl` - Havok Skeleton
* `.skp` - Bone Part Names (?)
* `.iks`
* `.ikb` - IK (?) (FlatBuffer Files) - determined from `skeletonparam` file
    * `body_bending` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/BDYB_BodyBendingBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_BodyBending.bt)
    * `bonamik_shared_params` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/BNMS_BonamikSharedParamsBinary.fbs)
    * `dialogue_lookat` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/DGLK_DialogueLookAtBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_DialogueLookAt.bt)
    * `eye_blink` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/EYEB_EyeBlinkBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_EyeBlink.bt)
    * `hit_reaction` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/HITR_HitReactionBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_HitReaction.bt)
    * `lod_setup` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/LODB_LodBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_LODBinary.bt)
    * `ride_posture` - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/IKB/RIDE_RidePostureBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_ikb_RidePosture.bt)
* `.kdb` - KineDriver Binary - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/KDB_KineDriverBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_kdb_KineDriverBinary.bt)
* `.bnmb` - Bonamik Binary - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/BNMB_BonamikBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_bnmb_Bonamik.bt)
* `.bnfb` - Bonamik F (?) Binary - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/BNFB_BonamikFBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_bnmb_Bonamik.bt)
* `.bnwb`
* `.lsb` - Lipsync (Silent?) Binary (FlatBuffer file) - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/LSDB_LipsyncSilentDataBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/LSDB_LipsyncSilentDataBinary.fbs)
* `.lmb` - Lipsync (Common?) Binary (FlatBuffer file) - [FlatBuffer Schema](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files.FlatBuffers/LMDB_LipsyncCommonDataBinary.fbs) / [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_bnfb_BonamikFBinary.bt)

!!! note
    If you want to convert FlatBuffer files to json, get [flatc](https://github.com/google/flatbuffers/releases) and run:

    * `flatc.exe --raw-binary --strict-json -t <path to .fbs schema file> -- <path to .kdb file>` to convert to json
    * `flatc -b <path to .fbs schema file> <path to .json file>` to convert back.

## Fonts
* `.fnt` - Font - [010 Editor Template](https://github.com/KillzXGaming/FF16-010-Templates/blob/main/FNT.bt)
* `.ker` - Kerning Data

## Sounds

* `.sab` - Square Enix Audio Binary
* `.mab`

## Cutscenes

* `csb` - Cutscene Binary - [010 Editor Template](https://github.com/Nenkai/010GameTemplates/blob/main/Square%20Enix/Final%20Fantasy%2016/FF16_csb_CutsceneBinary.bt)

## Localization
* `.pzd` - Panzer Localization - [010 Editor Template](https://github.com/KillzXGaming/FF16-010-Templates/blob/main/PZD.bt)

## UI
* `.uib` - UI Layout - [010 Editor Template](https://github.com/AlexPlaceres/FF16Templates/blob/main/Incomplete/uib.bt)
* `.utexpt` - UI Texture Part - [010 Editor Template](https://github.com/AlexPlaceres/FF16Templates/blob/main/Incomplete/utexpt.bt)