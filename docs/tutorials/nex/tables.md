---
icon: material/table
---

# :material-table: Nex Tables

!!! note

    This is far from complete.

### Ability Tables

* `command`
* `fatalattack`
* `phoenixshiftmove` - Phoenix shift parameters
* `skill`

### Entity Tables

* `actorbase`
* `bnpcbase`
* `enpcbase`
* `weaponbase`
* `gimmickbase`
* `stagesetbase`
* `nullactorbase`
* `animalbase`
* `propbase`

??? note "Internal category id to entity type"
    * 0 / 0xxxxxx - actorbase
    * 1 / 1xxxxxx - bnpcbase
    * 2 / 2xxxxxx - enpcbase
    * 3 / 3xxxxxx - weaponbase
    * 4 / 4xxxxxx - gimmickbase
    * 5 / 5xxxxxx - stagesetbase
    * 6 / 6xxxxxx - (Seemingly unused)
    * 7 / 7xxxxxx - nullactorbase
    * 8 / 8xxxxxx - animalbase
    * 9 / 9xxxxxx - propbase

### Game State Tables
* `usersituation` - Game/player progress states in general, a very important table. Each row is a condition which can be refered by other tables as unlock/lock flags.

### Graphics Configuration Tables

* `graclutterquality` - Clutter Quality
* `graenableambientocclusion` Ambient Occlusion
* `graenablebloomeffect` - Bloom Effect
* `graenablechromaticaberration` - Chromatic Aberration
* `graenablessr` - SSR
* `graenablevignette` - Vigneting
* `graframeraterational` - Framerate Rational
* `gralevelofdetailquality` - LOD Quality
* `gralodocclusioncullingtype` - LOD Occlusion Culling Type
* `gramotionblurintensity` - Motion Blur Itensity
* `graphicscloudsettings` - Cloud Settings
* `graphicsenvironmentparam` - Environment Params
* `graqualitypreset` - Quality Presets
* `graqualitypresetoverridesetting` - Quality Preset Override settings
* `graqualitypresetsettingparam` - Quality Preset Setting params
* `graqualitypresetsrsetting` - Quality Preset Super Resolution Setting
* `graqualitypresetsrsettingpar` Quality Preset Super Resolution Setting params
* `graqualitypresetsrtype` - Quality Preset Super Resolution Type
* `grashadowquality` - Shadow Quality
* `grasradaptivedr` - Super Resolution Adaptive DR
* `grasrframegeneration` - Super Resolution Frame Gen
* `grasrupscalealgorithm` Super Resolution Upscale Algorithm
* `grasrupscalepreset` Super Resolution Upscale Preset
* `grastreamingcorrectiontype` - Streaming Correction Type
* `graterrainquality` - Terrain Quality
* `gratexturequality` - Texture Quality
* `gravariablerateshading` - Variable Rate Shading
* `grawaterquality` - Water Quality

### Item Tables

* `equipitem` - Equippable items. >= 100000 (otherwise use item table)
* `item` - Items. (internally, this table is used when the id being fetched is < 100000).
* `useitem` - Usable items (potions, etc).

### Map/Level Tables

* `access` - World map item interaction (and more?)
* `accessmessage` - World object interaction for message prompt (tavern papers, etc)
* `areadefine`
* `gamemap` - Defines all the levels/maps in the game and which master map file `.mpb` they point to.
* `layoutsettings`
* `placement` - World map related
* `placename` - World map places names, used for just about everything
* `specialarea` - Defines special areas in maps, including walk/ui/battle restrictions.

### Model Tables

* `eid`
* `model` - Defines models in the game, usually pointed to by entity tables
* `modelcoordinate`

### Quest Tables

* `quest` - Defines all quests in the game (main/side)
* `questcharalayout`
* `questsequence` - Quest states/stages

### Reward Tables
* `droptable`

### World/Menu Map

* `worldmapanchor`

### Other

* `difficultylevel` - Difficulty settings
* `orchestrion` - Hideaway orchestrion/bgm listing
* `smobdirector` - Monster Hunt Board
* `loadingimage` - Loading screen images/background
* `resultcompletemessage` - Message to show when a fight is over
