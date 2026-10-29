---
title: Pulse
status: shipped
public_ready: true
version: 1.2.2
build: 8
---

# pulse

Reviewed: 2026-10-29

A macOS menu-bar utility that sends periodic I/O to selected external drives to help prevent standby. Built for editors, colorists, audio engineers, photographers, and anyone whose external drive spins down mid-session.

Product page: [Pulse](https://pulse.ifthis.app/) · [Handbook](https://pulse.ifthis.app/docs) · [Privacy](https://pulse.ifthis.app/privacy) · [Terms](https://pulse.ifthis.app/terms)

## Why
Keeping the Mac awake and keeping an external drive active are separate tasks. Pulse provides individual external-drive controls and optional Mac idle-sleep prevention. [Amphetamine also offers per-drive activity through Drive Alive](https://apps.apple.com/us/app/amphetamine/id937984704?mt=12). [macOS has separate system-sleep and disk-sleep settings](https://support.apple.com/guide/mac-help/set-sleep-and-wake-settings-mchle41a6ccd/mac), without a per-drive chooser. Drive behavior depends on the enclosure and connection.

## How

Pulse lists connected external drives, including detected volumes that are not mounted. Turn a drive **On** to mount it normally and request periodic writes to a tiny hidden heartbeat file (`.pulse-heartbeat`). New installs default to **20 seconds**; valid saved intervals are preserved. Choose 15, 20, 30, 60, or 120 seconds in Preferences. Longer intervals may allow standby; the best interval depends on the drive and enclosure.

The switch shows your requested setting. Pulse displays scheduled, pending, slow, or failed requests separately from the time of the last successful write. Slow requests remain pending until they finish, without starting overlapping heartbeats for that drive. Turn a drive **Off** to stop future heartbeats while leaving it mounted; a request already underway may still finish. Eject is a separate command in Arrange Drives.

A successful write confirms completed I/O, not that the drive has kept spinning between writes. Pulse shows standby prevention as unverified and does not promise a universal interval or zero drive wear.

**Keep Mac awake** is a separate option in Preferences, off by default. When enabled, it prevents automatic idle system sleep while Pulse is running, even without a drive heartbeat. The display can still sleep. It does not prevent manual Sleep, lid-close sleep, or other system-enforced sleep.

Jolt provides explicit recovery for supported drives; it cannot repair every USB or enclosure failure. Pulse monitors macOS thermal-pressure tiers rather than numeric temperature. After sustained serious or critical pressure it asks whether you are still editing; no reply within two minutes pauses Pulse's heartbeats and releases its Mac-awake request until you explicitly resume. The Mac and drives may then sleep. Pulse never closes your editing app or automatically ejects the drive.

## Documentation and calibration beta

The [Pulse Handbook](https://pulse.ifthis.app/docs) covers installation, editing workflows, drive and request states, mount/Jolt/Eject, Mac sleep, thermal protection, licensing, troubleshooting, and updates.

The current public download is **1.2.2 (build 8)**. **Pulse 1.3 is under review and is not included in that download.** Its per-drive profiles and optional **automatic calibration (Beta)** are documented separately in the handbook. The beta measures finite marker-request responsiveness for a drive and connection; it does not certify drive health, continuous rotation, a universally optimal interval, or editing-app reliability.

In the 1.3 review version, new drives, including SSDs, start Off. Automatic uses eligible per-drive test evidence or an explicitly uncalibrated 20-second starting interval. Advanced provides 20/40/60-second presets and custom values; the user starts calibration from the selected drive in Preferences. These controls do not describe the shared interval selector in the current 1.2.2 release.

## Install

Requires **macOS 14 or later** and an **Apple Silicon Mac**.

1. Download [`Pulse 1.2.2 (build 8)`](https://github.com/artseabra/glitch-os-public/releases/download/v1.2.2/Pulse.dmg).
2. Open the DMG and drag `Pulse.app` to `/Applications`.
3. Launch Pulse — look for the icon in your menu bar (no Dock icon).
4. Turn on the external drives you want mounted and receiving heartbeat activity.

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
See the [1.2.2 release notes](https://github.com/artseabra/glitch-os-public/releases/tag/v1.2.2) or the [Releases tab](https://github.com/artseabra/glitch-os-public/releases) for downloadable DMGs.
