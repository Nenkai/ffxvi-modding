---
icon: material/table
---

# :material-table: Nex Tables

!!! note

    This is far from complete considering there are over 800 tables.

### Ability/Movement Tables

* `attackparam` - Defines values & parameters for attacks
* `charatimelinevariation`
* `command`
* `customaction`
* `fatalattack`
* `jumpparam` - Defines jumping (field or battle) parameters
* `phoenixshiftmove` - Phoenix shift parameters
* `skill` - Links a UI Skill/Ability to a `command`, otherwise largely UI related parameters
* `shotcharge` - Charging fire & other abilities
* `summonpartspattern`
* `systemmove`

### Active Time Lore
* `loreworldviewnavigation`
* `lorecutmreference`
* `lorecutqreference`
* `loresynopsisreference`
* `loreworldviewnavigationcat`
* `loreworldviewnavigationstype`

### Arcade Mode Tables
* `scoreattackmode`
* `scoreattackstagerank`
* `uileaderboard`
* `telemetryleaderboardversion`

### AI Tables
* `aicounter`
* `aiparam`
* `aiaction`
* `aitask`
* `battleai`

### Animal Tables

* `animalbase`
* `animalbehaviorparam`
* `animalbehaviortype`
* `maptoanimaltable`

### Battle Tables
* `autoattackpack` - Monster related?
* `battleevent`
* `battlemessage` - Enemy ability messages i.e casts
* `battlescoreachieveddifficulty`
* `battlelayoutinfo` - ? Seen triggered when staggering
* `buddycommand` - Torgal controls
* `buff`
* `chancedowndamagerate` - Stagger?
* `damagereaction`
* `damagereactionreplacement`
* `damagereactionsize`
* `damagerate` - Unknown, seen used with Heaven's Cloud
* `directorbattleuitype`
* `directorgenerateheatmapinfo` - New enemies (?)
* `dpscheck`
* `emcameraparam`
* `emcorrectionparam`
* `guardresult`
* `hitvfx`
* `spreaddroptable` - Drops on field enemy killed
* `spreaddroptable`
* `stagerank` - Fired on abttle end
* `uidamagepopup`

#### Death
* `deadparam`
* `corpsebase`
* `corpsestay`
* `deadeffect`

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

### Obelisk / Fast Travel Tables
* `obelisk`

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
* `uiframelimitconfig`
* `uigamma`
* `uiresolutionconfig`

### Item Tables

* `equipitem` - Equippable items. >= 100000 (otherwise use item table)
* `item` - Items. (internally, this table is used when the id being fetched is < 100000).
* `useitem` - Usable items (potions, etc).

### Hunt/Mark Tables
* `smobdirector` - Defines hunts

### Map/Level Tables

* `astralprojection` - Aether Floods
* `access` - World map item interaction (and more?)
* `accessmessage` - World object interaction for message prompt (tavern papers, etc)
* `areadefine`
* `bnpcignorecollision` - Unknown. Seen used at the first bridge in rosaria, starting from three reeds 
* `directormodule`
* `gamemap` - Defines all the levels/maps in the game and which master map file `.mpb` they point to.
* `gimmickitemdrop` - Item Pickups on field
* `layoutsettings`
* `mapdirector`
* `mapdirectormodule`
* `mapdirectorsequenceset`
* `physicsobjectsound`
* `placement` - World map related
* `placename` - World map places names, used for just about everything
* `specialarea` - Defines special areas in maps, including walk/ui/battle restrictions.

### Model Tables

* `animpacexistface`
* `animpacexisthead`
* `characterskinid` - Defines the skin ids, used for `characterskincategory`. Can only be two enabled rows.
* `characterskincategory` - Arete Stone 'Appearance' Menu, every character. Hardcoded to id 0-4 (each character). There can only be two skins due to table design. (read `characterskincategory.layout` for more information).
* `characterskinmodelparam` - Points skins to a `modelcoordinate` row.
* `colorcoordinate`
* `eid`
* `eyecolor`
* `haircolor`
* `model` - Defines models in the game, usually pointed to by entity tables
* `modelcoordinate` - Coordinates/links models into their respective parts (body/face/head) & more.
* `skincolor`
* `weaponskincategory` - Arete Stone 'Appearance' Menu, weapon skins. Number of rows will match `c8001`, body folder.

### Physics Tables
* `ragdollparam`

### Party/Squad Tables

* `partyfollowback`
* `partyfollowdistance`
* `partyfollowformation`
* `partyfollowposition`
* `partyfollowspeedlimitgroup`
* `partyfollowspeedlimit`
* `partyfollowspeed`
* `partyobstacle`
* `partywarpposition`

### Quest/Cutscene Tables
* `defaulttalk`
* `destinationmarkerparam` - Sets a destination marker
* `maindefaulttalksequence`
* `quest` - Defines all quests in the game (main/side)
* `questcharalayout`
* `questdefaulttalksequence`
* `questcutscene`
* `questsequence` - Quest states/stages
* `questreportjump` - Fast travel to NPC for task sequence completion
* `simpleevent`
* `simpleeventpartylocationset`
* `simpleeventlocationoffset`
* `useimportantitemstodo` - Giving items to NPCs

### Player Stat Tables
* `paramgrow` - Player Levels

### Reward Tables
* `droptable`

### Sound Tables
* `bgmchangedefine` - Handles bgm changes
* `jingle`
* `orchestrion` - Hideaway orchestrion/bgm listing
* `simpleeventbgmvolume` - Unknown, used alongside resultcompletemessage
* `soundreverbparam` - Used for reverb line of dialogue (i.e hooded man speaks to clive)

### Hall of Virtue/Training Tables
* `trainingenemy`

### Thousand Tomes
* `loredictionaryalias`
* `loredictionaryexp`
* `loredictionarypickup`
* `loredictionarycategory`
* `loredictionarytagcategory`
* `loredictionarytag`
* `uimemorandumsearchname`

### Tutorial Tables
* `howto` - Tutorial messages/states
* `tutorial` - Battle Tutorial (start of game, Rosalith Castle with Lord Commander Murdoch)

### UI Tables (Misc)
* `uiaddon` - Defines assets to use for UIs along with additional parameters (character input & more)
* `uiannounce` - Defines alerts/errors with a red banner i.e 'Unable to craft', 'Insufficient materials'
* `uicolor`
* `uifocusinfo`
* `uipadguide` - Controller Settings
* `uisummonaction`
* `uitooltip`
* `window`

### World/Menu Map
* `fieldmapobelisk`
* `worldmapanchor`
* `uifieldmapicon`

### Other

* `brooch` - Seals
* `caption`
* `difficultylevel` - Difficulty settings
* `guidancecameraparam` - Camera guiding, i.e used when petting torgal
* `moviedata` - Defines available cutscene/movie assets in the game
* `replay` - Stage Replay Mode
* `speaker` - Defines names for entities, used for ingame enemy names for instance
* `speakerset`
* `loadingimage` - Loading screen images/background
* `resultcompletemessage` - Message to show when a quest/fight is over

### Unused Tables

These tables are known to not be used at all (at least in retail builds).

* `attackelement`
* `achievement`
* `actorstate`
* `actorstateset`
* `aiactionselectorcondition`
* `animalgroupid`
* `areatype`
* `bardssonglist`
* `contentdynamicparam`
* `footstep`
* `gamemapfieldtype`
* `gamemapbuildresult`
* `magic`
* `mapdirectorflag`
* `mergegrid`
* `onlinesuiteeventtype`
* `patchdlcversion`
* `shopcamera`
* `squad`
* `systemparam`
* `titlecount`
* `userpermission`
* `uicharactersacttype`
* `uicharacterslargecategory`
* `ztext`

## Union Codes

Union codes are used by columns that can reference other tables. They usually appear right before the actual ID columns.

* `0` = ?
* `23` = questcharalayoutbnpc
* `25` = ?
* `41` = ?
* `46` = defaulttalk
* `50` = questcharalayoutenpc
* `55` = layoutnamedinstance
* `79` = ?
* `82` = ?
* `99` = itemshopbase
* `100` = smithshopbase
* `114` = sidequestbattledirector
* `127` = item
* `131` = partytalk
* `135` = droptable
* `146` = bgmmode
* `147` = placename
* `192` = cutsceneset
* `204` = questprogress
* `256` = partymember
* `266` = Icon Id?
* `273` = worldmapanchor
* `277` = usersituation
* `314` = bgmselect
* `316` = moviedata
* `330` = ?
* `373` = ?
* `375` = mapdirectorsequence
* `382` = ?
* `399` = directoractorlist
* `428` = ?
* `454` = ?
* `458` = usersituationflag
* `484` = shopchronicle
* `486` = ?
* `487` = ?
* `488` = shoppastsight
* `491` = ?
* `494` = ?
* `502` = stageshopbase
* `517` = ?
* `523` = shoplore
* `528` = ?
* `545` = ?
* `557` = ?
* `577` = ?
* `568` = directoractormonitor
* `649` = ?
* `655` = ?
* `664` = captionfreeword
* `719` = shopmythril
* `818` = shopfixedpaletteexit
* `831` = cutsceneconnect
* `845` = maindefaulttalksequence
* `846` = questdefaulttalksequence
* `847` = questsimpleventsequence
* `856` = simpleevent
* `889` = ?
* `935` = directormovecustomspeedparam
* `942` = simpleeventselect
* `957` = shopquestcounter
* `976` = shopfixedpaletteaccess
* `977` = shopfixedpalettewarp
* `978` = fixedpalette
* `985` = questdiscardlist
* `989` = icondiscovery
* `998` = shopfamevalue
* `1011` = ?
* `1027` = ?
* `1044` = ?
* `1047` = abysseffect
* `1138` = ?
* `1249` = abyssboostparam
* `1255` = ?