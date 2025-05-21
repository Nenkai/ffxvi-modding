---
icon: material/table
---

# :material-table: Nex Tables

!!! note

    This is far from complete considering there are over 800 tables.

??? tip "About `DLCFlags` column"

    This is used to 'hide' or 'show' columns depending on dlc entitlement. **TLDR: `10020` = Echoes of the Fallen, `10030` = The Rising Tide.**
     
    When the nex database is loaded, `dlcentitlement` is fetched & entitlement verified to check for listed dlcs and sets global's bit flags. Unlock bit 2 = `dlcentitlement`   id 2, Unlock bit 4 = `dlcentitlement` id 3

    Then, `dlcentitlement` (1019), `dlcitem` (1009) and `dlcpathlist` (1021) are marked as whitelisted rows, where all rows are available regardless of `DLCFlags`.

    Finally the game goes a specific set of `DLCFlags`. For each `DLCFlags`, the game goes through all tables and each row. In order:

    * `10080` - Unknown, included by default
    * `10040` - Unknown, included by default
    * `10092` - Unknown, included by default
    * `10010` - If dlc unlock bits is 1 (always 1 by default).
    * `10060` - Unknown, included by default
    * `10020` - If dlc unlock bits has 2 (Echoes of the Fallen)
    * `10070` - Unknown, included by default
    * `10030` - If dlc unlock bits has 4 (The Rising Tide)
    * `10050` - Unknown, included by default

    Handling happens at `sub_140805C00` (ffxvi.exe 1.0.1 steam). Signature: `48 89 5C 24 ? 48 89 6C 24 ? 48 89 74 24 ? 57 48 83 EC ? 44 0F B6 81`

??? tip "About `Comment` column"

    This would normally contain row 'names' or columns which was stripped by SQEX for release. More importantly it may have been used by them to better display row links in excel by using this column as a name.

    `FF16Tools` may automatically include comments which may be defined in `.layout` files. **Please contribute!**

??? tip "VFX Audio Ids"

    Some tables may refer to a "VFX Audio Id". These refer to entries present within `.vatb` files.

    `.vatb` or VFX Audio Table Binary simply maps specified ids to a VFX & Audio file combination. The game simply search through the currently registered vatb files for a matching id.

You can find more comments in each table's [layout](https://github.com/Nenkai/FF16Tools/tree/master/FF16Tools.Files/Nex/Layouts) definition.

### Ability/Movement Tables

* `attackparam` - Defines values & parameters for attacks
* `charatimeline` - Defines chara timeline files (*.tlb), which defines the timelines for each move.
* `charatimelinevariation`
* `combo`
* `command`
* `commandactionset`
* `customaction`
* `fatalattack`
* `jumpparam` - Defines jumping (field or battle) parameters
* `playermode`
* `playercommandbuilder`
* `phoenixshiftmove` - Phoenix shift parameters
* `skill` - Links a UI Skill/Ability to a `command`, otherwise largely UI related parameters
* `shotcharge` - Charging fire & other abilities
* `summonpartspattern`
* `summonparts`
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
* `bnpcreactiontype`
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
* `stagerank` - Fired on abttle end
* `uidamagepopup`

### Cutscene Tables
* `cutsceneset` - Defines an actual cutscene, not just a conversation between two entities (`simpleevent`)
* `scenariocutscene` (Id 0-10000 and 1000000-1099999)
* `scenariocutscenetimeline`
* `levelcutscene` (Id 10000-19999 and 2000000-2099999)
* `levelcutscenetimeline`
* `levelevent` (Id 60000-69999)
* `leveleventtimeline`
* `synopsis` (Id 70000-79999)
* `synopsistimeline`
* `battleevent` (Id 80000-89999)
* `battleeventtimeline`
* `questcutscene` (Id 4000000-4099999)
* `questcutscenetimeline`

!!! tip
    Some ids will point directly to PZD/Localization entries in the `nxd/text` folder.
    
    For example, `questcutscene` id 4000200 -> `nxd/text/cutq/cutq4000200.pzd`.
    
#### Death
* `deadparam`
* `corpsebase`
* `corpsestay`
* `deadeffect`

#### Director Tables

Note: Union Id 48 (directortype) may select one of these.

* `mapdirector`
* `tutorialdirector`
* `systemassistdirector`
* `fieldeventdirector`
* `smobdirector` - Defines hunts
* `sidequestbattledirector`
* `missionbattledirector`
* `battledirector`
* `behavioreventdirector`
* `battleblockdirector`
* `fixedpalettedirector`
* `abyssgatedirector`

### Crafting/Shop Tables
* `recipe`
* `shopbase`
* `smithshopbase`
* `stageshopbase`

## DLC Tables
* `dlcitem` - Defines DLC & Claimable Items
* `dlcentitlement`
* `patchdlcversion`

### Entity Tables

* `actorbase`
* `bnpcbase`
* `enpcbase`
* `weaponbase` - Defines weapon models
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
* `mapdirectormodule`
* `mapdirectorsequenceset`
* `physicsobjectsound`
* `placement` - World map related
* `placename` - World map places names, used for just about everything
* `specialarea` - Defines special areas in maps, including walk/ui/battle restrictions.

### Model Tables

* `animpacexistface`
* `animpacexisthead`
* `body`
* `characterskinid` - Defines the skin ids, used for `characterskincategory`. Can only be two enabled rows.
* `characterskincategory` - Arete Stone 'Appearance' Menu, every character. Hardcoded to id 0-4 (each character). There can only be two skins due to table design. (read `characterskincategory.layout` for more information).
* `characterskinmodelparam` - Points skins to a `modelcoordinate` row.
* `colorcoordinate`
* `eid` - Links certain ids to model joints (refer to comments in eid.layout)
* `eyecolor`
* `face`
* `footwetness` - Points to additional parts in each model (.mdl) file
* `haircolor`
* `head`
* `mastsparam`
* `model` - Defines models in the game, usually pointed to by entity tables
* `modelcoordinate` - Coordinates/links models into their respective parts (body/face/head) & more.
* `partadditionaldataparam`
* `skincolor`
* `weaponskincategory` - Arete Stone 'Appearance' Menu, weapon skins. Number of rows will match `c8001`, body folder.

!!! tip

    For paths, refer to the `body` and `head` keys. So `180100101` = `1801 001 01` => `c1801`, `b001`, `_1`.


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

### Quest Tables
* `defaulttalk`
* `destinationmarkerparam` - Sets a destination marker
* `maindefaulttalksequence`
* `quest` - Defines all quests in the game (main/side)
* `questcharalayout`
* `questdefaulttalksequence`
* `questsequence` - Quest sequences/parts. Grouped by `quest` ids. Essentially the current state for a `quest`.
* `questreportjump` - Fast travel to NPC for task sequence completion
* `simpleevent` - Defines a regular discussion/event between clive/NPC
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

### Stage Replay
* `replay` - Stage Replay Mode

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
* `uiarray` - Defines ui lists for (hardcoded) ui situations
* `uiannounce` - Defines alerts/errors with a red banner i.e 'Unable to craft', 'Insufficient materials'
* `uicolor`
* `uifocusinfo`
* `uimenu`
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

!!! note

    May be behind, check the [enum list](https://github.com/Nenkai/FF16Tools/blob/master/FF16Tools.Files/Nex/NexEnums.cs) here for an updated list.

* `0` = value argument
* `3` = action
* `15` = result
* `17` = attackparamid
* `23` = bnpcbase
* `25` = directorbankitemid
* `27` = eid
* `41` = ?
* `42` = command
* `46` = defaulttalk
* `48` = type of director
* `50` = enpcbase
* `55` = layoutnamedinstance
* `58` = attacktype (link between equipitem & atktype)
* `79` = quest
* `82` = questsequence
* `99` = itemshopbase
* `100` = smithshopbase
* `105` = charatimelinevariation
* `112` = equipment_index (not an actual table, but 0 = sword, etc)
* `114` = sidequestbattledirector
* `124` = item
* `127` = levelcutscene
* `131` = partytalk
* `135` = droptable
* `138` = behavioreventactionset
* `143` = buff
* `146` = bgmmode
* `147` = placename
* `177` = equipitem
* `192` = cutsceneset
* `198` = transition
* `204` = questprogress
* `208` = summonmode
* `256` = partymember
* `260` = scenariocutscene
* `266` = Icon Id?
* `273` = worldmapanchor
* `277` = usersituation
* `282` = levelevent
* `312` = battleevent
* `314` = bgmselect
* `316` = moviedata
* `317` = gamemap
* `330` = ?
* `344` = normalcameraparam2 (same as normalcameraparam?)
* `359` = missionbattledirector
* `363` = uicolor
* `366` = normalcameraparam
* `373` = astralprojection
* `375` = mapdirectorsequence
* `382` = directorfaketargetsettings
* `399` = directoractorlist
* `403` = behaviormovesequence (or behaviormoveset)
* `428` = ?
* `454` = battletag
* `458` = usersituationflag
* `484` = shopchronicle
* `486` = layoutgroup (entity group ids from map binary/mpb)
* `487` = letterlist (not an actual game table)
* `488` = shoppastsight
* `491` = ?
* `494` = battleblockdirector
* `496` = caption
* `502` = stageshopbase
* `517` = collectionlist (not an actual game table)
* `523` = shoplore
* `524` = battletalk
* `528` = howto
* `530` = tutorialdirector
* `539` = behaviorwaitparam
* `545` = tutorial
* `557` = directorcondition
* `568` = directoractormonitor
* `577` = mapdirectorflag
* `632` = skill
* `639` = behavioreventactionsequence
* `649` = ?
* `653` = behaviormoverailparam
* `655` = mapdirectorsequence
* `664` = captionfreeword
* `665` = directorforwardmoveparam
* `668` = questcharalayoutbnpc
* `692` = smobdirector
* `700` = systemassisttimertalkitem
* `706` = layoutenpcinstance
* `719` = shopmythril
* `722` = behaviorlinkmovetarget
* `742` = telemetryobjectset,
* `758` = telemetrypropertyvalue,
* `791` = letter
* `793` = telemetryobject
* `818` = shopfixedpaletteexit
* `831` = cutsceneconnect
* `841` = questcutscene
* `843` = mainpartytalksequence
* `844` = questpartytalksequence
* `845` = maindefaulttalksequence
* `846` = questdefaulttalksequence
* `847` = questsimpleventsequence
* `848` = mainsimpleeventsequence
* `854` = behavioreventdirector
* `856` = simpleevent
* `861` = synopsis
* `884` = simpleeventmarkerpoint
* `889` = orchestrionlist (not an actual game table)
* `890` = orchestrion
* `917` = simpleeventlightpreset
* `932` = questcharalayoutenpc
* `934` = directorshipswingparameter
* `935` = directormovecustomspeedparam
* `942` = simpleeventselect
* `943` = simpleeventsequencerandomset
* `945` = cutsceneconnectquestseqarg
* `957` = shopquestcounter
* `976` = shopfixedpaletteaccess
* `977` = shopfixedpalettewarp
* `978` = fixedpalette
* `985` = questdiscardlist
* `989` = icondiscovery
* `998` = shopfamevalue
* `1011` = ?
* `1012` = loresynopsysreference
* `1027` = envvoice
* `1044` = ?
* `1047` = abysseffect
* `1079` = lorecutmreference
* `1080` = lorecutqreference
* `1138` = fieldmapobelisk
* `1144` = dlcentitlement
* `1174` = patchdlcversion
* `1186` = simpleeventlightpresetselect
* `1249` = abyssboostparam
* `1255` = ?