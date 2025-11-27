# Common Timeline Elements

Common timeline element ids all follow the same pattern (0xxx).

These are the timeline elements that can appear in all kinds of timelines.

## Known common timeline elements

??? note "`0008` - `CameraAnimationRange`"
    #### Used to animate the camera.

??? note "`0010` - `BattleCondition`"
    #### Unknown / WIP
    
??? note "`0012` - `BulletTimeRange`"
    #### Unknown / WIP

??? note "`0017` - `ControlPermission`"
    #### Used in character timelines to configure which action types can cancel the currently playing timeline. Each parameter is a different action type that can either cancel the currently playing timeline (if it's 1), or not (if it's 0).
        Parameters (in order):
        movement_actions
        movement_input
        Unknown_0x80
        turn_possible_target_angle_update
        turn_update_possible
        combo_attack_action
        combo_impossible_action
        jump
        avoidance
        basic_weapon_action_burning_blade
        unique_weapon_action
        shot_action
        summon_action
        other_actions
        ---
        unknown parameters

??? note "`0031` - `PlaySoundTrigger`"
    #### Unknown / WIP

??? note "`0033` - `AttachWeaponTemporaryRange`"
    #### Unknown / WIP

??? note "`0045` - `ModelSE`"
    #### Unknown / WIP
    
??? note "`0047` - `BattleMessageRange`"
    #### Unknown / WIP

??? note "`0051` - `EnableDestructorCollision`"
    #### Unknown / WIP

??? note "`0057` - `PadVibration`"
    #### Unknown / WIP

??? note "`0074` - `ControlRejectionRange`"
    #### Unknown / WIP
