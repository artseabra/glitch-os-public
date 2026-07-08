# glitch-os (public)

Reviewed: 2026-07-08
Status: public release surface
Brand surface: [sn.ifth.is/defrag](https://sn.ifth.is/defrag)

glitch-os is Art Seabra's toolkit of small, sharp utilities for creative work.

This public repository only carries published, public-ready apps and their signed / notarized release artifacts. Development source, internal instructions, and unreleased work live outside this public surface.

## Published Apps

| App | What it does | Status | Download |
| --- | --- | --- | --- |
| [`pulse`](./defrag/pulse) | macOS menu-bar utility that keeps specific external drives awake through real I/O activity. | v1.0.0 | [Pulse.dmg](https://github.com/artseabra/glitch-os-public/releases/download/v1.0.0/Pulse.dmg) |

Each published app has its own subdirectory with a product-facing README.

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
