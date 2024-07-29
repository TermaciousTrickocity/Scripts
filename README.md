# Timed Checkpoint Loop
> Plays nicely with theater film playback.

```css
(script continuous void reiko_needs_a_checkpoint
    (sleep_until
        (begin
            (sleep (* 30.0 60.0 2.0)) ; Will trigger every two minutes!
            (game_save_no_timeout)
            false
        )
    )
)
```

# Player input trigger
> Useful for instances where you don't have the menu option to trigger a revert to last checkpoint. (Multiplayer)
```css
(script continuous void reiko_needs_a_checkpoint
    (if (player_action_test_dpad_up)
        (begin
            (chud_post_message_hack "Saving...")
            (game_save_no_timeout)
            (player_disable_movement true)
            (sleep (* 30.0 60.0 0.02)) ; Two second delay for montage editors using theater.
            (player_disable_movement false)
            (player_action_test_reset)
        )
    )
    (if (player_action_test_dpad_down) 
        (begin
            (chud_post_message_hack "Reverting...")
            (sleep 5)
            (game_revert)
            (player_action_test_reset)
        )
    )
)
```

## Checkpoint Types
Disregards all player's current situation and saves. (Be very careful! You cannot delay this type of checkpoint.)
```
(game_save_immediate)
```

Checks to see if it's safe to save the game, then saves. (It'll never give up. You can delay this type of checkpoint forever.)
```
(game_save_no_timeout)
```

Check to see if it's safe to save the game, then saves. (It'll give up after 8 seconds.)
```
(game_save)
```

Causes the player to resume from the most recent checkpoint.
```
(game_revert)
```

## Skulls
### Enable/Disable
```css
(skull_enable skull_name boolean)
```
Example:
```css
(skull_enable skull_tilt true)
(skull_enable skull_tilt false)
```
## Skull Types
### Iron
> The Iron skull causes the mission to restart if the player dies during the campaign for whatever reason. On campaign Cooperative Play, if even one player dies everyone is forced to revert back to the last reached checkpoint. In Firefight, the skull disables respawning after the player died.
```
(skull_iron)
```
### Black Eye
> The Black Eye skull causes the automatic regeneration of the player's energy shields to be disabled. The only way to recharge the energy shields is to melee or perform assassination on an enemy.
```
(skull_black_eye)
```
### Tough Luck
> The Tough Luck skull causes enemies to evade vehicles, dodge grenades and heavy weapon projectiles.
```
(skull_tough_luck)
```
### Catch
> The Catch skull causes the frequency in which AI-controlled characters throw grenades to be doubled, while also always dropping two grenades upon death.
```
(skull_catch)
```
### Cloud/Fog
> The Cloud skull is a new skull featured in Halo: Reach, replacing the Fog skull in Halo 3. Just like the Fog skull, the Cloud skull causes the player's motion tracker to be disabled.
```
(skull_fog)
```
### Famine
> The Famine skull causes all dropped weapons' ammunition or charge to be reduced by 50%. Weapons stored in crates and Spartan Lasers are unaffected.
```
(skull_famine)
```
### Thunderstorm
> The Thunderstorm skull causes enemies' ranks to increase.
```
(skull_thunderstorm)
```
### Tilt
> The Tilt skull exaggerates the strengths and weaknesses of weapons.
```
(skull_tilt)
```
### Mythic
> The Mythic skull causes enemies to have twice as much health than they normally would.
```
(skull_mythic)
```
### Assassin
```
(skull_assassin)
```
### Blind
> The Blind skull causes the player's first person HUD, including the scoring box, weapon and arms, to disappear.
```
(skull_blind)
```
### Cowbell
> The Cowbell skull increases physics effects three-fold.
```
(skull_superman)
```
### Grunt Birthday Party
> The Grunt Birthday Party skull causes headshots on Grunts to explode in a shower of confetti as well as producing a sound clip of children cheering.
```
(skull_birthday_party)
```
### IWHBYD
> The IWHBYD (I Would Have Been Your Daddy) skull causes rare and secret dialog to appear throughout the campaign and turns off normal dialog.
```
(skull_daddy)
```
### Red
> Custom skull
```
(skull_red)
```
### Blue
> Custom skull
```
(skull_blue)
```
### Yellow
> Custom skull
```
(skull_yellow)
```
