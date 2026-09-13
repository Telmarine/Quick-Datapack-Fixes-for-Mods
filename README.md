# createdeco-placard-fix

Datapack override for **Create Deco 2.1.3**.

## Bug

Create Deco's shipped `data/createdeco/recipe/placard.json` (the "dye placard back to white" recipe) used `"id"` as an ingredient key:

```json
{"tag": "createdeco:placards"}, {"id": "minecraft:white_dye"}
```

Minecraft 1.21.x's ingredient codec only accepts `"tag"` or `"item"` inside a recipe's `ingredients` array — `"id"` is only valid inside a recipe's `result` object. This threw a `JsonParseException` on every server start, and the recipe silently failed to load.

## Fix

Swap `"id"` for `"item"`:

```json
{"tag": "createdeco:placards"}, {"item": "minecraft:white_dye"}
```

Verified: recipe loads with zero errors, recipe count increments correctly, and the recipe is confirmed working in JEI and in-game.

## Install

Copy this folder's contents into `world/datapacks/createdeco-placard-fix/` and restart the server.

## When to delete this branch

Once Create Deco ships an official fix for this recipe upstream, this branch (and the datapack folder on your server) is no longer needed.
