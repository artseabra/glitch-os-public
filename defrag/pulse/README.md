---
title: Pulse
status: shipped
public_ready: true
version: 1.2.0
build: 5
---

# pulse

Reviewed: 2026-10-28

A macOS menu-bar utility that keeps specific external drives awake via real I/O activity. Built for editors, colorists, audio engineers, photographers, and anyone whose external drive spins down mid-session.

Product page: [`sn.ifth.is/defrag/pulse`](https://sn.ifth.is/defrag/pulse)

## Why
Existing menu-bar caffeine apps (Amphetamine, Theine, KeepingYouAwake) keep the **system** awake but do nothing at the drive layer. macOS's "Put hard disks to sleep" checkbox is a global hammer with no per-drive control and is ignored by many USB enclosures. Pulse fills that gap.

## How

Pulse lists connected external drives, including detected volumes that are not mounted. Turn a drive **On** to mount it normally and keep it awake with a tiny hidden heartbeat file (`.pulse-heartbeat`), every 30 seconds by default. Turn it **Off** to stop Pulse's heartbeats while leaving the drive mounted. Eject is a separate command in Arrange Drives.

Jolt provides explicit recovery for supported drives; it cannot repair every USB or enclosure failure. Pulse monitors macOS thermal-pressure tiers rather than numeric temperature. After sustained serious or critical pressure it asks whether you are still editing; no reply within two minutes pauses Pulse's heartbeats until you resume. The drive may sleep. Pulse never closes your editing app or automatically ejects the drive.

## Install

Requires **macOS 14 or later** and an **Apple Silicon Mac**.

1. Download [`Pulse 1.2.0 (build 5)`](https://github.com/artseabra/glitch-os-public/releases/download/v1.2.0/Pulse.dmg).
2. Open the DMG and drag `Pulse.app` to `/Applications`.
3. Launch Pulse — look for the icon in your menu bar (no Dock icon).
4. Turn on the external drives you want mounted and kept awake.

## Distribution
- Signed with Developer ID Application + hardened runtime
- Notarized via Apple, stapled, Gatekeeper-accepted
- No analytics, no telemetry, no network calls beyond Polar licensing

## Verifying a release
```bash
xcrun stapler validate Pulse.dmg
spctl --assess --type open --context context:primary-signature -v Pulse.dmg
```

## Releases
See the [1.2.0 release notes](https://github.com/artseabra/glitch-os-public/releases/tag/v1.2.0) or the [Releases tab](https://github.com/artseabra/glitch-os-public/releases) for downloadable DMGs.
