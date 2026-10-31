# Minecraft AI Companion

A Minecraft Java Edition LAN companion built with Mineflayer and a Fabric in-game task hub.

## Current audited source

- **Latest snapshot:** v0.8.2
- **Minecraft target:** Java 1.21.11 + Fabric
- **Requirements:** Node.js 20+, Java 21 for Fabric source
- **Source archive:** [Download v0.8.2 public source](releases/minecraft-ai-companion-v0.8.2-public-source.zip)
- **All retained version archives:** [Download the v0.1.0–v0.8.2 archive bundle](releases/minecraft-ai-companion-release-archives-v0.1.0-to-v0.8.2.zip)

The release ZIP contains the complete project folder (Mineflayer bot, dashboard, Fabric task hub source, tests and documentation). The repository keeps the downloadable source snapshot in the `releases/` directory; the source is not yet expanded into individual root-level files.

## Documentation

- [Changelog and historical release ledger](CHANGELOG.md)
- [v0.8.2 audit report](AUDIT-REPORT.md)
- [License](LICENSE)

## Quick start

1. Download and extract the v0.8.2 source ZIP.
2. Copy `.env.example` to `.env`.
3. Set `MC_HOST`, `MC_PORT`, `MC_USERNAME`, and the exact `MC_OWNER_NAME`.
4. Run `npm install`, then `npm run check`, then `npm start`.
5. Build the Fabric task hub with Java 21 and Gradle, then install its JAR with Fabric API in the Minecraft 1.21.11 Fabric profile.

See the source ZIP's README and `fabric-task-hub/README.md` for full setup.

## Security

Never commit `.env`, API keys, access tokens, passwords, Minecraft account credentials, or world backups. The published source includes only `.env.example`. Keep the dashboard bound to loopback unless you add authentication and transport security.

## Verification status

The v0.8.2 source passed its local check suite: **22 tests passed, 0 failed**. This does not constitute a live Minecraft integration test. Node runtime dependencies were not available in the audit environment, the Fabric mod was not compiled there, and no LAN world was available. See [AUDIT-REPORT.md](AUDIT-REPORT.md).
