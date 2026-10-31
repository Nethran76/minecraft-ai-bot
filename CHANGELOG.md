# Changelog and Release History

This ledger is based on the retained ZIP archives and the README/metadata inside them. Historical ZIPs are retained in the development workspace; they have not yet been uploaded as GitHub release assets. This initial repository documentation does not fabricate separate historical Git commits.

## v0.8.2 — 2026-10-31 — audited source baseline

**Added / changed**
- Fail-closed owner authorization for in-game chat: an unset `MC_OWNER_NAME` no longer lets the first LAN player claim control.
- Validation for empty commands and a maximum command length of 256 characters.
- Expanded the Fabric task hub and web dashboard to 37 action buttons.
- Fixed the short `pearl` command sent by the GUI so it is recognized by the parser.
- Renamed the misleading potion action to `Brewing Check`, accurately reflecting that it audits a nearby stand and ingredients rather than automating brewing slots.
- Expanded help text and regression coverage, including checking that each Fabric button command maps to a parser and TaskManager handler.

**Audit**: `npm run check` passed with 22 tests and no failures; JavaScript syntax checks, JSON parse checks, HTML smoke checks, Fabric button mapping/dispatch checks, and ZIP integrity checks passed. This was not a live Minecraft test. Node runtime dependencies were unavailable, Gradle was unavailable, and a Minecraft LAN server was not available. See [AUDIT-REPORT.md](AUDIT-REPORT.md).

## Historical releases

| Version | Retained archive | Documented focus / additions |
|---|---|---|
| v0.1.0 | `minecraft-ai-companion-v0.1.0.zip` | Starter Mineflayer bot, LAN connection settings, dashboard telemetry, deterministic parser, follow/come/stop/home, bounded nearby block collection, pause/resume/stop, basic health/food and lava safety, reconnect behavior. |
| v0.2.0 | `minecraft-ai-companion-v0.2.0.zip` | Survival controller, optional LLM command interpreter, task planning (including diamond armour plan), persistent local world memory, starter house template. |
| v0.2.1 | `minecraft-ai-companion-v0.2.1-armor-equip.zip` | Armour-equipping follow-up snapshot. |
| v0.2.2 | `minecraft-ai-companion-v0.2.2-tools-food.zip` | Tool progression and food-related commands; README says wooden tools and a stone pickaxe can be crafted when materials and workspace are available. |
| v0.2.3 | `minecraft-ai-companion-v0.2.3-lan-ip.zip` | LAN connection configuration snapshot. |
| v0.3.0 | `minecraft-ai-companion-v0.3.0-autonomous-mining.zip` | Bounded autonomous mining expeditions, loaded-chunk ore scanning and reachable waypoint exploration. |
| v0.4.0 | `minecraft-ai-companion-v0.4.0-survival-inventory.zip` | Survival/inventory improvements and chest-storage workflow. |
| v0.4.1 | `minecraft-ai-companion-v0.4.1-in-game-chat.zip` | `!bot` chat command control and bot chat replies. Historical docs allowed first-player claim when owner was blank; v0.8.2 replaced this with fail-closed owner authorization. |
| v0.5.0 | `minecraft-ai-companion-v0.5.0-full-survival.zip` | Expanded full-survival feature snapshot. |
| v0.6.0 | `minecraft-ai-companion-v0.6.0-advanced-combat.zip` | Combat/movement expansion, with experimental Elytra, mace, spear/Lunge and Trial Chamber-oriented support. |
| v0.7.0 | `minecraft-ai-companion-v0.7.0-all-upgrades.zip` | Consolidated upgrade snapshot and expanded command/progression support. |
| v0.8.0 | `minecraft-ai-companion-v0.8.0-task-hub.zip` | In-game task hub snapshot. |
| v0.8.1 | `minecraft-ai-companion-v0.8.1-mc1.21.11-fabric.zip` | Fabric 1.21.11 task hub source alongside the Mineflayer bot. |
| v0.8.2 | `minecraft-ai-companion-v0.8.2-final-audited.zip` | Owner authentication, command validation, 37 task buttons, pearl parser regression fix, clarified brewing action, expanded checks and audit report. |

## Known limitations recorded in historical documentation

- v0.1.0 collection was limited to a configured nearby search radius; it did not autonomously branch-mine or travel across the world to find every vein.
- v0.2.x documentation says the starter house builder is a fixed template, does not terraform or remove obstructions, and armour crafting requires a nearby crafting table and ingredients. Automatic furnace smelting/resource acquisition were not fully implemented.
- v0.3.0 mining was bounded to loaded chunks and reachable routes; it could not guarantee world-wide ore discovery or every vein.
- v0.4.0 documentation says chest storage had not been live-tested against the target server/modpack.
- v0.4.1 historical configuration allowed first-player chat claim if the owner was blank; superseded by v0.8.2 fail-closed owner authorization.
- v0.5/v0.6 documentation flags incomplete Nether/End progression and experimental combat/movement; PvP victory, Elytra landing, mace hits, water clutches and complete Trial Chamber clears were not guaranteed.
- v0.8.2 limitations are in [AUDIT-REPORT.md](AUDIT-REPORT.md): brewing is audit-only, PvP is basic, pearl/wind-charge are one-shot actions, scans are loaded-chunk/visible-entity bounded, and Nether/End commands report readiness rather than completing progression.

The retained READMEs do not provide a reliable bug-fix list for every historical patch release. Where a specific fix is not stated in an archive, this changelog records the documented release focus and known limitations rather than inventing fixes.
