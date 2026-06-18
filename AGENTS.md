# AGENTS.md — CobblemonShortcuts

## Cobblemon API reference (READ THIS BEFORE TOUCHING COBBLEMON CODE)

Cobblemon's real source + curated API notes live in a **shared** folder one level up:

```
C:\DEV\Mods\_cobblemon-ref\
  README.md            <- start here
  source\              <- full Cobblemon 1.7.3 source: GREP THIS for exact signatures
  battle-gui.md        <- the battle UI API (this mod's main hook) + 2v2 target-selection gotcha
  api-index.md         <- where to find things in source/
  setup-and-gotchas.md <- build/dependency/Kotlin-vs-Java traps
```

Rules:
- **Never invent a Cobblemon method name.** If it isn't in `_cobblemon-ref\source\`, it doesn't
  exist in this version — grep the source instead of guessing.
- This mod is the battle-shortcuts use case; `battle-gui.md` documents the exact flow,
  including the open 2v2 bug (commit `54f977f`): the move→target transition must pass
  `gimmickID` and `gimmickMove`, not `null, null`.

## Build / versions

Cobblemon 1.7.3 · MC 1.21.1 · official Mojang mappings · Java 21 · Fabric.
Cobblemon is `modCompileOnly` (Kotlin-metadata bug breaks the dev runtime) — test by building
and running in the real Prism instance (`copyToMods` task), not `runClient`.

## Project rule

Every time you update this mod, increase the build version (`mod_version` in `gradle.properties`).
