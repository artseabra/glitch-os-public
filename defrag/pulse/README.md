---
title: Pulse
status: shipped
public_ready: true
version: 1.2.1
build: 6
---

# pulse

Reviewed: 2026-10-28

A macOS menu-bar utility that keeps specific external drives awake via real I/O activity. Built for editors, colorists, audio engineers, photographers, and anyone whose external drive spins down mid-session.

Product page: [`sn.ifth.is/defrag/pulse`](https://sn.ifth.is/defrag/pulse)

## Why
Keeping the Mac awake and keeping an external drive active are separate tasks. Pulse provides individual external-drive controls and optional Mac idle-sleep prevention. [Amphetamine also offers per-drive activity through Drive Alive](https://apps.apple.com/us/app/amphetamine/id937984704?mt=12). [macOS has separate system-sleep and disk-sleep settings](https://support.apple.com/guide/mac-help/set-sleep-and-wake-settings-mchle41a6ccd/mac), without a per-drive chooser. Drive behavior depends on the enclosure and connection.

## How

Pulse lists connected external drives, including detected volumes that are not mounted. Turn a drive **On** to mount it normally and keep it awake with a tiny hidden heartbeat file (`.pulse-heartbeat`), every 30 seconds by default. Turn it **Off** to stop Pulse's heartbeats while leaving the drive mounted. Eject is a separate command in Arrange Drives.

**Keep Mac awake** is a separate option in Preferences, off by default. When enabled, it prevents automatic idle system sleep while Pulse is running, even without a drive heartbeat. The display can still sleep. It does not prevent manual Sleep, lid-close sleep, or other system-enforced sleep.

Jolt provides explicit recovery for supported drives; it cannot repair every USB or enclosure failure. Pulse monitors macOS thermal-pressure tiers rather than numeric temperature. After sustained serious or critical pressure it asks whether you are still editing; no reply within two minutes pauses Pulse's heartbeats and releases its Mac-awake request until you explicitly resume. The Mac and drives may then sleep. Pulse never closes your editing app or automatically ejects the drive.

## Install

Requires **macOS 14 or later** and an **Apple Silicon Mac**.

1. Download [`Pulse 1.2.1 (build 6)`](https://github.com/artseabra/glitch-os-public/releases/download/v1.2.1/Pulse.dmg).
2. Open the DMG and drag `Pulse.app` to `/Applications`.
3. Launch Pulse — look for the icon in your menu bar (no Dock icon).
4. Turn on the external drives you want mounted and kept awake.

## Distribution
- Signed with Developer ID Application + hardened runtime
- Notarized via Apple, stapled, Gatekeeper-accepted
- The Mac app sends no usage analytics or drive activity telemetry; Polar handles licensing

## Verifying a release
```bash
xcrun stapler validate Pulse.dmg
spctl --assess --type open --context context:primary-signature -v Pulse.dmg
```

## Releases
See the [1.2.1 release notes](https://github.com/artseabra/glitch-os-public/releases/tag/v1.2.1) or the [Releases tab](https://github.com/artseabra/glitch-os-public/releases) for downloadable DMGs.
