---
icon: material/table
---

# :material-table: Nex Tables

!!! note

    This is far from complete considering there are over 800 tables.

### Ability/Movement Tables

* `attackparam` - Defines values & parameters for attacks
* `command`
* `charatimelinevariation`
* `fatalattack`
* `phoenixshiftmove` - Phoenix shift parameters
* `skill` - Links a UI Skill/Ability to a `command`, otherwise largely UI related parameters

### AI Tables
* `aicounter`
* `battleai`

### Crafting/Shop Tables
* `recipe`
* `shopbase`
* `smithshopbase`
* `stageshopbase`

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

### Event Tables
* `simpleevent`

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

* `colorcoordinate`
* `eid`
* `eyecolor`
* `haircolor`
* `model` - Defines models in the game, usually pointed to by entity tables
* `modelcoordinate`
* `skincolor`

### Physics Tables
* `ragdollparam`

### Quest Tables

* `quest` - Defines all quests in the game (main/side)
* `questcharalayout`
* `questsequence` - Quest states/stages

### Reward Tables
* `droptable`

### Sound Tables
* `jingle`
* `orchestrion` - Hideaway orchestrion/bgm listing

### Tutorial Tables
* `howto`

### UI Tables
* `uiaddon` - Defines assets to use for UIs along with additional parameters (character input & more)
* `uicolor`
* `uifieldmapicon`
* `uisummonaction`
* `window`

### World/Menu Map

* `worldmapanchor`

### Other

* `caption`
* `difficultylevel` - Difficulty settings
* `moviedata` - Defines available cutscene/movie assets in the game
* `smobdirector` - Monster Hunt Board
* `speaker` - Defines names for entities, used for ingame enemy names for instance
* `speakerset`
* `loadingimage` - Loading screen images/background
* `resultcompletemessage` - Message to show when a fight is over

## Unused Tables

These tables are known to not be used at all (at least in retail builds).

* `magic`
* `mergegrid`
* `systemparam`
* `userpermission`
* `ztext`