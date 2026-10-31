# Minecraft AI Companion

A Minecraft Java Edition LAN companion built with Mineflayer and a Fabric in-game task hub.

## Project status

- Latest audited snapshot: **v0.8.2**
- Minecraft target: Java 1.21.11 + Fabric
- Requirements for the full project: Node.js 20+; Java 21 and Gradle for the Fabric mod
- Repository visibility: Public

## Documentation

- [Changelog and historical release ledger](CHANGELOG.md)
- [v0.8.2 audit report](AUDIT-REPORT.md)
- [MIT License](LICENSE)

## Source import status

This repository currently contains the release documentation and audit ledger. The full v0.8.2 source tree and historical ZIP archives have **not yet been committed to GitHub**. The latest source snapshot is available in this conversation as a downloadable archive; it is not currently a GitHub release asset. No download link to a nonexistent repository file is shown here.

## v0.8.2 quick-start outline

1. Extract the v0.8.2 source archive.
2. Copy `.env.example` to `.env`.
3. Set `MC_HOST`, `MC_PORT`, `MC_USERNAME`, and the exact `MC_OWNER_NAME`.
4. Run `npm install`, then `npm run check`, then `npm start`.
5. Build the Fabric task hub with Java 21 and Gradle, then install its JAR with Fabric API in the Minecraft 1.21.11 Fabric profile.

See the source archive's README and `fabric-task-hub/README.md` for full setup.

## Security

Never commit `.env`, API keys, access tokens, passwords, Minecraft account credentials, or world backups. Publish only `.env.example`. Keep the dashboard bound to loopback unless you add authentication and transport security.

## Verification status

The v0.8.2 source passed its local check suite: **22 tests passed, 0 failed**. This does not constitute a live Minecraft integration test. Node runtime dependencies were not available in the audit environment, the Fabric mod was not compiled there, and no LAN world was available. See [AUDIT-REPORT.md](AUDIT-REPORT.md).
