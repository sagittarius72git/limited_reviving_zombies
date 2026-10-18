# Limited_Reviving_Zombies

A mod that limits zombie revival instead of banning it. Revived zombies come back weaker and slower depending on how damaged the corpse is, and they don't rise a second time.
It only affects monsters whose species is ZOMBIE (self-repairing robots and the like are left alone).

This mod (including its documentation) was made largely with the help of Claude Opus. Tested on stable v0.12 and experimental v260922.

## What it changes

- Disables `REVIVES_HEALTHY`: no zombie rises at full strength anymore.
- HP on revival: the base game revives them at 70% of max HP ÷ (corpse damage + 1). This mod lowers undamaged corpses to 65%.
- Downed and stunned right after rising: time to smash their head.
- Rigor mortis (`lrz_rigor`): their speed drops for a while.
- One revival only: kill a revived zombie and its corpse never rises again.

| Corpse damage | HP on revival | Helpless time | Rigor mortis | Speed penalty |
|---|---|---|---|---|
| 0 (undamaged) | 65% | 5 seconds | 2 minutes | -10 |
| 1 | 35% | 12 seconds | 5 minutes | -20 |
| 2 | ~23% | 20 seconds | 8 minutes | -30 |
| 3 (mangled) | 17.5% | 30 seconds | 12 minutes | -40 |

The time until revival (about 6–24 hours) is unchanged from the base game.

## Settings

Edit `mod.cfg` at the top of `main.lua` (`max_revivals` = number of revivals, 0 disables revival). Changes apply mid-game with **Reload Lua Code** in the debug menu.
The speed penalty is `speed_mod` in `effects.json` and needs a world reload.

## Notes

- **Requires a Lua-enabled build** (`lua_api_version: 2`).
- Don't use it together with `No_Reviving`.
- You can add it to an existing world, but corpses already on the map revive normally the first time after you add it.
- Zombies you revive yourself as zombie slaves are not affected.
