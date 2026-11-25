# S4Studio — Public Tester Build (Alpha & Beta)

A desktop hub to manage an S4 League private server: client, sources, processes, database,
content, packages, plugins, AI assistant and web dashboard.

> **This repository hosts ONLY the test build.** The source code stays private (team repo):
> see the public project page at [Suplic0z05/S4Studio](https://github.com/Suplic0z05/S4Studio)
> for documentation, architecture and the tester guide.

---

## How to become a tester

> **⚠ Beta not ready for download yet.** The Releases section is still empty: the beta
> build will be published here only once it passes the team's stability checks.
> You can apply now — licenses are assigned and the first wave gets access at release.

1. Get a **license key** from the team (format `S4T1.….…`) — it is personal, time-limited
   (**1 week**) and tracked: keys are **limited in number**. To request one, open an issue
   here with the *Tester application* template (top-right **New issue**).
2. When the beta is published: download `S4StudioSetup.exe` from the **Releases** section.
3. Run the installer → it picks the install path → downloads the official runtimes (.NET,
   MariaDB) **verifying their hashes** → extracts the app and **seals** it (integrity manifest).
4. On first launch, enter your key: without a valid key (not expired, not revoked)
   **the app does not start**.
5. After expiry the app deactivates itself: no project file is recoverable through the app.
   Renewal = a new key from the team (or joining the team, which unlocks continuous access).

## Requirements

- Windows 10/11 x64 (the .NET 10 runtime and MariaDB are downloaded by the installer with
  verified hashes)
- No prior knowledge required: the first-run wizard only asks for two folders
  (the client folder with `S4Client.exe` + `resource.s4hd`, and the sources folder)

## What to test (in priority order)

1. **Installation** (installer, first launch, wizard) and **database setup**
   (MariaDB with the official hash)
2. **Database**: connection, schema, players, backups
3. **Shop Wizard** and `shop.check` (client ↔ DB item consistency)
4. **Client**: opening `resource.s4hd`, text preview, extraction, import, save with backup
5. **Web Admin Console**: login, TOTP, commands
6. Anything else: open an **Issue** here with logs (data folder → `Data/machine/logs`)

## What you get as a tester

- Early builds before wider distribution, with changelogs
- A direct line to the developer: your reports shape the roadmap
- Credit in release notes for findings that lead to fixes
- Hands-on practice with the tool before anyone runs it on a live server

## Tester rules

- The key is personal: do not share it (it is tracked and can be revoked)
- No anti-cheat is ever touched: the project contains no cheat/inject features
- Test only on servers/databases you own or are authorized to use
- Report through issues, one issue per problem, and **never paste passwords,
  tokens or AI keys** — logs only, from the relevant section

## The beta cooldown (how the 1-week window works)

The beta build uses a **sliding 7-day cooldown** instead of a hard expiration:

- at **every launch** (every visit) the cooldown **restarts from that moment**: the app is
  always usable for the next 7 days, however often you reopen it;
- the window is persisted encrypted (DPAPI) and shown in the license status file, so the
  team can see when a key was last visited;
- this works only while the key signature is valid and the key is not revoked — revocation
  stays an immediate, unconditional block;
- known, declared limit: on a single PC the window is anchored to the system clock; the
  team server (online verification, next step) will overwrite the local window when
  reachable.

## License & integrity (how the build is protected)

- Builds are **sealed**: `installation-manifest.json` with a SHA-256 per file and a protected
  digest (the installer verifies it; the app refuses altered files)
- Licenses are **cryptographically signed** (RSA-3072): altering or extending a key without
  the team key is mathematically infeasible
- Known, declared limit: the app trusts the system clock — without online verification a
  skilled user can move the clock; online verification is the next step (the team server
  overrides the local expiry when reachable)

---
Project: S4Studio · alpha channel · © team S4Studio — reserved for authorized testers
