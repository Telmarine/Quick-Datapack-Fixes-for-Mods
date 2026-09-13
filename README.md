# veggiesdelight-loot-fix

Datapack override for **VeggiesDelight 1.9.3**.

## Bug

All 9 of VeggiesDelight's shipped `farmersdelight:add_loot_table` loot modifiers (in `data/veggiesdelight/loot_modifiers/`) used the field name `"lootTable"`:

```json
{"type": "farmersdelight:add_loot_table", "conditions": [...], "lootTable": "veggiesdelight:chests/vd_abandoned_mineshaft"}
```

NeoForge's `GlobalLootModifier` deserializer for this modifier type expects the field to be named `"table"` — confirmed by extracting Farmer's Delight's own shipped example of the identical modifier type directly from its jar. Because `"lootTable"` isn't a recognized field, all 9 modifiers silently failed and none of VeggiesDelight's produce ever got added to the targeted vanilla loot tables (abandoned mineshafts, pillager outposts, shipwrecks, simple dungeons, and 5 village house variants).

## Fix

Rename the field to `"table"` in all 9 files. Content is otherwise byte-identical to VeggiesDelight's originals.

Verified: fresh log after restart shows the exact expected warning-count drop and zero recurrence of any of the 9 original error lines. The VeggiesDelight developers have also been notified of the upstream bug directly.

## Install

Copy this folder's contents into `world/datapacks/veggiesdelight-loot-fix/` and restart the server.

## When to delete this branch

Once VeggiesDelight ships an official fix for these loot modifiers upstream, this branch (and the datapack folder on your server) is no longer needed.
