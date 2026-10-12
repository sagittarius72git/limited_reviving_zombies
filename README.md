# Limited_Reviving_Zombies (CDDA 0.I port)

A port of the BN mod "Limited_Reviving_Zombies" to Cataclysm: DDA stable 0.I-1 (Ito-1). It runs on JSON (EOCs) only.

A mod that limits zombie revival instead of banning it. Revived zombies come back weaker and slower depending on how damaged the corpse is, and they don't rise a second time.
It only affects monsters whose species is ZOMBIE.

## What it changes

- Disables `REVIVES_HEALTHY`: no zombie rises at full strength anymore.
- Caps HP on revival: if the game's own result is lower, that wins, so this only ever makes them weaker.
- Downed and stunned right after rising: time to smash their head.
- Rigor mortis (`lrz_rigor`): their speed drops for a while.
- One revival only: kill a revived zombie and its corpse never rises again.

| Corpse damage | HP cap | Helpless time | Rigor mortis | Speed penalty |
|---|---|---|---|---|
| 0 (undamaged) | 65% | 5 seconds | 2 minutes | -10 |
| 1 | 50% | 12 seconds | 5 minutes | -20 |
| 2 | 35% | 20 seconds | 8 minutes | -30 |
| 3 (mangled) | 25% | 30 seconds | 12 minutes | -40 |

The time until revival is unchanged from the base game.

## Settings

Edit `lrz_hp_ratio` / `lrz_rise_secs` / `lrz_rigor_mins` at the top of `eoc.json`. Set `lrz_max_revivals` to 0 and killed zombies stay down.
The speed penalty is `speed_mod` in `effects.json`. Both need a world reload.

## Differences from the BN version

- Revivals can only be 0 or 1 (CDDA can't carry the corpse's record over to the revived monster).
- Corpse damage is guessed from the HP right after rising. Burnt corpses count as more damaged.
- Corpses of revived zombies that die with no attacker (standing in fire or acid, and so on) are not sealed.
- A revived zombie is detected as "at 70% HP or less when first seen". A zombie hurt right after it appears may be treated as revived too.

## Notes

- You can add it to an existing world. Zombies that had already revived before you added it may rise once more. Zombies already hurt when you add it are treated as revived.

## Credits

- Author: sagittarius72
- This mod (including its documentation) was made largely with the help of Claude Opus.

Assisted-by: Claude:claude-opus-5-5
