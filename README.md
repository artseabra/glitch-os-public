# glitch-os (public)

Reviewed: 2026-10-28
Status: public release surface
Brand surface: [sn.ifth.is/defrag](https://sn.ifth.is/defrag)

glitch-os is Art Seabra's toolkit of small, sharp utilities for creative work.

This public repository only carries published, public-ready apps and their signed / notarized release artifacts. Development source, internal instructions, and unreleased work live outside this public surface.

## System Position

Pulse is a shipped Studio utility, not a primary ÆrrSystem front-door surface. Public identity should point to Pulse directly when the utility matters, and avoid using glitch-os as the headline.

## Published Apps

| App | What it does | Status | Download |
| --- | --- | --- | --- |
| [`pulse`](./defrag/pulse) | macOS menu-bar utility for selected external-drive activity, with optional Mac idle-sleep prevention. | v1.2.2 (build 8) | [Pulse.dmg](https://github.com/artseabra/glitch-os-public/releases/download/v1.2.2/Pulse.dmg) |

Each published app has its own subdirectory with a product-facing README.
Pulse 1.2.2 requires macOS 14 or later and an Apple Silicon Mac. New installs use a 20-second heartbeat interval; valid saved intervals are preserved. Drive standby behavior depends on the drive and enclosure. Its separate **Keep Mac awake** option is off by default.

## Public-Readiness Gate

An app appears in this repo only after it ships a signed, notarized release. The gate is explicit:

- `public_ready: true` in the app's own `README.md` frontmatter
- Signed with a Developer ID Application certificate
- Notarized via Apple
- Stapled with the notarization ticket
- Verified to pass `spctl --assess` (Gatekeeper)

## Verifying A Release

```bash
xcrun stapler validate Pulse.dmg
spctl --assess --type open --context context:primary-signature -v Pulse.dmg
```

## Public Boundary

This repo is the public shelf, not the full workshop. If a tool is not listed here, it has not passed the public-readiness gate.

## Links
- Defrag toolkit: https://sn.ifth.is/defrag
- Pulse product page: https://sn.ifth.is/defrag/pulse
- Builder: https://sn.ifth.is/art
