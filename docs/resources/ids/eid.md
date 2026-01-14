# Eid

Eids are essentially **body part ids**.

A [chara collision binary](../formats/ccb.md) (`.ccb`) and optionally, a model file (`.mdl`, though MCEX data type 9) declares every Eid that can be used within a model - it connects a joint to a Eid.

Their behavior is consistent between models and the game may directly access a joint through an hardcoded Eid. 

[FaithFramework](https://www.nexusmods.com/finalfantasy16/mods/138) can be used to display the current Eids for the current controlled actor.

TODO: Make a list of body part names for each Eid.