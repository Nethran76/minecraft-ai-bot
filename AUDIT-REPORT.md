# v0.8.2 Release Audit

Target: Minecraft Java 1.21.11 + Fabric, Java 21, Node.js 20+

## Changes in this audit release

- Added fail-closed Minecraft chat owner authorization. A blank `MC_OWNER_NAME` no longer lets the first LAN player claim bot control.
- Added command input validation (non-empty, maximum 256 characters).
- Expanded the Fabric in-game task hub and browser dashboard with 37 action buttons.
- Fixed recognition of the short `pearl` command sent by the GUI.
- Renamed the misleading "Brew Potions" button to "Brewing Check": the current implementation audits ingredients and detects a nearby stand.
- Expanded `!bot help` and documented feature limits.

## Checks run

| Check | Result |
|---|---|
| `npm run check` | PASS |
| Node syntax checks across 17 JavaScript files | PASS |
| Node automated tests | 22 passed, 0 failed |
| JSON metadata parse | 3 files passed |
| HTML parser smoke check | PASS |
| Fabric task-hub buttons parsed and dispatched by TaskManager | 37 checked, 0 unknown / 0 missing handlers |
| ZIP integrity | PASS |

The audit found two regressions: the Fabric GUI sent `pearl`, but the parser did not recognize that short form; and the Fabric task-hub command list needed an end-to-end static check against TaskManager dispatch handlers. Both are fixed/covered by regression tests.

## Checks not possible in the audit environment

- `npm install` did not complete; runtime dependencies (`mineflayer`, `express`, `socket.io`) were not installed. The Node dashboard and live Mineflayer runtime were not started.
- Gradle was unavailable, so the Fabric Java source was not compiled and no installable mod JAR was produced.
- No Minecraft 1.21.11 LAN server was available. Bot connection, combat, mining, inventory, brewing, movement and GUI interaction were not integration-tested in-game.

## Known functional limitations

- Brewing is an ingredient/station audit, not automatic brewing-stand slot control.
- PvP is a basic follow-and-attack routine, not advanced human-level combat.
- Pearl and Wind Charge are one-shot item actions, not tactical teleport/movement planning.
- Healing depends on available food or detectable healing-potion NBT; potion metadata varies.
- Elytra launch, water clutch, mace and spear behavior are experimental and require disposable-world testing.
- World scans see loaded chunks and visible entities only.
- Nether/End commands report readiness; they do not autonomously complete all progression.
- Fabric buttons report whether the local dashboard accepted the command, not whether the bot completed it.

## User setup

1. Copy `.env.example` to `.env`.
2. Set `MC_OWNER_NAME` to the exact Minecraft Java username.
3. Set `MC_HOST` to the host address shown when opening the LAN world, and set `MC_PORT` to the port Minecraft displays.
4. Keep `MC_VERSION=1.21.11`, `MC_AUTH=offline`, and dashboard host `127.0.0.1` for the local setup.
5. Run `npm install`, `npm run check`, then `npm start`.
6. Build the Fabric source with Java 21 and Gradle; install the resulting non-sources JAR plus Fabric API.
7. Back up the Minecraft world before testing automation.
