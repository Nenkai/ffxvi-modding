# Character Timelines

These timelines use common elements (0xxx), as well as special elements unique to this timeline category (1xxx).

## Known character timeline elements

??? note "`1001` - `PlayCharacterAnimation`"
    #### Used to play an animation given an .anmb file on the character executing the timeline.
        Parameters:
        Anim - Path to the .anmb file containing the animation to play

??? note "`1002` - `EnableAttackParam`"
    #### Used to activate hitboxes on the character executing the timeline, setting a desired AttackParamId to inflict on the target upon collision.
        Parameters:
        AttackParamId

??? note "`1007` - `StopAllVerticalMomentum`"
    #### Used to interrupt all current vertical movement, and prevent any further of it.  

??? note "`1008` - `EnableStompExecution`"
    #### Used to allow the player to execute a Stomp (Jump Cancel) to cancel the currently playing character animation and reset airborne actions.

??? note "`1010` - `TurnToTarget`"
    #### Unknown / WIP

??? note "`1012` - `MagicCreate`"
    #### Used to create an instance of a magic object given the MagicId. For this to execute correctly, the MagicId must point to a spell correctly included inside the character's .magic file. 
        Parameters:
        UnkId / MagicId

??? note "`1016` - `PrecedeInputUnk`"
    #### Unknown / WIP

??? note "`1021` - `TriggerPrecisionEvasion`"
    #### While enabled, getting hit during certain animations (such as Dodge and Rook's Gambit) triggers the precision effect. Can follow up with another action automatically.

??? note "`1023` - `PlayVisualOrSoundEffects`"
    #### Used to spawn VFX or SFX at the position of the character executing the timeline.
        Parameters:
        VFX - Path to the .vfxb file containing the visual effects to play
        SE - Path to the file containing the sound effect to play

??? note "`1030` - `PlayVisualOrSoundEffects2`"
    #### Used to spawn VFX or SFX at the position of the character executing the timeline.
        Parameters:
        VFX - Path to the .vfxb file containing the visual effects to play
        SE - Path to the file containing the sound effect to play

??? note "`1035` - `PlayFacialAnimation`"
    #### Used to play a facial animation given an .anmb file on the character executing the timeline.
        Parameters:
        Anim - Path to the .anmb file containing the facial animation to play

??? note "`1047` - `SummonPartsVisibileRange`"
    #### Unknown / WIP

??? note "`1049` - `PlayVisualOrSoundEffects3`"
    #### Used to spawn VFX or SFX at the position of the character executing the timeline.
        Parameters:
        VFX - Path to the .vfxb file containing the visual effects to play
        SE - Path to the file containing the sound effect to play

??? note "`1053` - `BattleVoiceTrigger`"
    #### Unknown / WIP

??? note "`1058` - `DisableReceiver`"
    #### Unknown / WIP

??? note "`1086` - `TriggerUpwardMomentumOnAttack`"
    #### While enabled, landing a successful attack on a target will move the user upwards and keep them in the air for a given number of frames.

??? note "`1097` - `DisableCharaUnk`"
    #### Unknown / WIP

??? note "`1117` - `ActionEventTrigger`"
    #### Unknown / WIP
