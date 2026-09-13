# Quick-Datapack-Fixes-for-Mods

Standalone, non-destructive Minecraft datapack overrides that patch bugs shipped inside third-party mod jars, for a NeoForge 1.21.1 (build 21.1.250) server. Each fix lives on its own branch, named after the mod it patches, so it can be pulled in or deleted independently once that mod's developer ships an official fix upstream.

## Branches

- [`createdeco-placard-fix`](../../tree/createdeco-placard-fix) — Create Deco 2.1.3: corrects the placard dye-back recipe (invalid `id` ingredient key -> `item`).
- [`veggiesdelight-loot-fix`](../../tree/veggiesdelight-loot-fix) — VeggiesDelight 1.9.3: corrects the field name in 9 loot-table injection modifiers (`lootTable` -> `table`).

Check out the branch for the fix you need — each one's root *is* a ready-to-install datapack folder (a `pack.mcmeta` plus the corrected `data/...` tree). See that branch's own README for the specific bug, before/after JSON, and verification notes.

## Why branches instead of folders

Each of these fixes patches a bug in someone else's mod. Once that mod's developer ships a real fix, the corresponding branch here is dead weight — delete the branch and it's gone, with zero effect on any other fix.

## General installation

1. Check out the branch for the fix you want.
2. Copy the branch's contents into a new folder under your world's `datapacks/` directory, e.g. `world/datapacks/createdeco-placard-fix/`.
3. Restart the server.
4. Delete the folder (and restart) to revert, or delete the branch once it's no longer needed.
