# Pirate Town - Minecraft World Save

A single-player/small-server Minecraft world: an overworld region set and nothing else. No code, no
build files, no plugins or datapacks - this folder is game data, saved from a Paper 1.21.8 server
and named after the build it holds. Kept here as a backup and as the source for the map.

**Suggested repo name:** `piratetown-world`
**Stack:** Anvil region format (`level.dat` + `region/*.mca`); world last written by Paper 1.21.8 (`1.21.8-R0.1-SNAPSHOT`)
**Status:** data only
**Last modified:** 2026-09-01

## What it does

Nothing - it is a world folder. What is inside:

- `level.dat` - gzip-compressed NBT: `LevelName` is `world`, `ServerBrands` records Paper,
  `Bukkit.Version` `Paper/1.21.8-60-29c8822 (MC: 1.21.8)`, plus spawn point, game type, world border
  and generator settings.
- `region/` - 26 `.mca` region files (~64 MB) spanning region coordinates x `-2..2` by z `-3..2`,
  i.e. roughly a 2560 x 3072 block area around the origin, minus a few ungenerated corners.
- No `DIM-1` / `DIM1`, so the Nether and End for this world were never generated or were pruned; no
  `stats/`, `advancements/`, `players/`, `datapacks/` or `poi/`.

## Layout

```
level.dat     world metadata (NBT, gzipped)
region/       r.<x>.<z>.mca overworld chunks
```

## Running it

Copy this folder into a Paper 1.21.x server's `worlds/` directory as `piratetown`, or drop it in as
a vanilla single-player save. `level.dat` reports Paper, so vanilla clients may complain about the
`ServerBrands`/`Bukkit.Version` tags but the chunks load normally.

## Notes

- Publishable as data, and every file is under GitHub's size limits, but ~64 MB of binary region
  files in git is worth a Git LFS branch or a release asset instead.
- A world folder can leak more than the build: `level.dat` stores the seed-adjacent generator
  settings and the spawn coordinates, and any map-item or banner art in the region files is part of
  the save. Nothing player-identifying is present here because the player data folders are absent.
