---
title: Pulse
status: shipped
version: 1.0.0
---

# pulse

A macOS menu-bar utility that keeps specific external drives awake via real I/O activity. Built for editors, colorists, audio engineers, photographers, and anyone whose external drive spins down mid-session.

Product page: [`sn.ifth.is/defrag/pulse`](https://sn.ifth.is/defrag/pulse)

## Why
Existing menu-bar caffeine apps (Amphetamine, Theine, KeepingYouAwake) keep the **system** awake but do nothing at the drive layer. macOS's "Put hard disks to sleep" checkbox is a global hammer with no per-drive control and is ignored by many USB enclosures. Pulse fills that gap.

## How
For each "pinned" drive, Pulse writes a tiny hidden heartbeat file (`.pulse-heartbeat`) every 30 seconds. Real I/O is the only reliable way to keep an external drive awake. DiskArbitration watches mount/unmount; pinned drives auto-resume on remount and auto-stop on eject.

## Install
1. Download [`Pulse.dmg`](https://github.com/artseabra/glitch-os-public/releases/download/v1.0.0/Pulse.dmg) from the latest release.
2. Open the DMG and drag `Pulse.app` to `/Applications`.
3. Launch Pulse — look for the icon in your menu bar (no Dock icon).
4. Pin the drives you want kept awake.

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
See the [Releases tab](https://github.com/artseabra/glitch-os-public/releases) for downloadable DMGs.
