# glitch-os (public)

Public-facing surface for **glitch-os** — Art Seabra's toolkit of small, sharp utilities for creative work.

This repo only carries **published, public-ready apps** and their signed/notarized release artifacts. The full development source — including in-progress tools, internal AGENTS instructions, and unreleased work — lives in a separate private repo and is intentionally not exposed here.

Brand surface: [`sn.ifth.is/defrag`](https://sn.ifth.is/defrag)

## Published apps

| App | What it does | Status | Download |
| --- | --- | --- | --- |
| [`pulse`](./defrag/pulse) | macOS menu-bar utility that keeps specific external drives awake via real I/O activity. For editors who lose drives mid-session. | ✅ v1.0.0 | [Pulse.dmg](https://github.com/artseabra/glitch-os-public/releases/download/v1.0.0/Pulse.dmg) |

Each published app has its own subdirectory with a product-facing README.

## Public-readiness gate

An app appears in this repo only after it ships a signed, notarized release. The gate is explicit:

- `public_ready: true` in the app's own `README.md` frontmatter
- Signed with a Developer ID Application certificate
- Notarized via Apple
- Stapled with the notarization ticket
- Verified to pass `spctl --assess` (Gatekeeper)

## Verifying a release

```bash
xcrun stapler validate Pulse.dmg
spctl --assess --type open --context context:primary-signature -v Pulse.dmg
```

## Links
- Defrag toolkit: https://sn.ifth.is/defrag
- Pulse product page: https://sn.ifth.is/defrag/pulse
- Builder: https://sn.ifth.is/art
