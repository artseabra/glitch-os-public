---
title: Pulse
status: shipped
public_ready: true
version: 1.3.1
build: 23
---

# pulse

Reviewed: 2026-10-31

A macOS menu-bar utility that sends periodic I/O to selected external drives to help prevent standby. Built for editors, colorists, audio engineers, photographers, and anyone whose external drive spins down mid-session.

Product page: [Pulse](https://pulse.ifthis.app/) · [Handbook](https://pulse.ifthis.app/docs) · [Privacy](https://pulse.ifthis.app/privacy) · [Terms](https://pulse.ifthis.app/terms)

## Why
Keeping the Mac awake and keeping an external drive active are separate tasks. Pulse provides individual external-drive controls and optional Mac idle-sleep prevention. [Amphetamine also offers per-drive activity through Drive Alive](https://apps.apple.com/us/app/amphetamine/id937984704?mt=12). [macOS has separate system-sleep and disk-sleep settings](https://support.apple.com/guide/mac-help/set-sleep-and-wake-settings-mchle41a6ccd/mac), without a per-drive chooser. Drive behavior depends on the enclosure and connection.

## How

Pulse lists connected external drives, including detected volumes that are not mounted. Internal disks, disk images and network shares stay out of the list. Turn a drive **On** to mount it normally and request periodic writes to a tiny hidden heartbeat file (`.pulse-heartbeat`). New drives, including SSDs, start **Off**; you choose which receive activity. Existing saved On choices and valid intervals are retained on upgrade.

Each drive has its own **manual interval**, initially **20 seconds**. This is a starting choice, not a tested or universally optimal recommendation. Advanced, beneath Interval in the selected drive's keep-awake card, offers **20 / 40 / 60 seconds** and a custom whole number from **5 to 3600 seconds**. Entering **0 turns that drive Off**; it never creates a zero-second timer. Saving an interval does not enable an Off drive. Longer intervals may allow standby; no interval is validated for every enclosure.

The switch shows your requested setting. Pulse displays scheduled, pending, slow, or failed requests separately from the time of the last successful write. Slow requests remain pending until they finish, without starting overlapping heartbeats for that drive. Turn a drive **Off** to stop future heartbeats while leaving it mounted; a request already underway may still finish. Eject is a separate command in Arrange Drives.

A successful write confirms completed I/O, not that the drive has kept spinning between writes. Pulse shows standby prevention as unverified and does not promise a universal interval or zero drive wear.

**Keep Mac awake** is a separate option in Preferences, off by default. When enabled, it prevents automatic idle system sleep while Pulse is running, even without a drive heartbeat. The display can still sleep. It does not prevent manual Sleep, lid-close sleep, or other system-enforced sleep.

Jolt provides explicit recovery for supported drives; it cannot repair every USB or enclosure failure. Pulse monitors macOS thermal-pressure tiers rather than numeric temperature. After sustained serious or critical pressure it asks whether you are still editing; no reply within two minutes pauses Pulse's heartbeats and releases its Mac-awake request until you explicitly resume. The Mac and drives may then sleep. Pulse never closes your editing app or automatically ejects the drive.

## Manual setup in 1.3.1

First-launch guidance explains that already-connected drives can stay plugged in. Select a drive in Settings, turn **Keep drive awake** On when you need activity, and choose its interval under **Advanced**. The setting applies only to that drive. A shorter interval sends requests more often; a longer interval creates a longer quiet gap. Observe how your drive behaves during normal work and choose a setting that suits it. Pulse does not run a diagnostic to select an interval.

The calibration engine and its tests, recommendations and controls have been **removed**, not hidden or left running in the background. On upgrade, former Automatic choices become 20 seconds; valid custom intervals and saved On/Off choices remain. Old calibration records are not used. The implementation is archived separately for possible future work.

The same rounded graphite Pulse icon now appears in the app, Settings, popover and menu bar. Ordinary heartbeats stay visually quiet. Manual Jolt may flash briefly; macOS Reduce Motion and thermal protection suppress that animation.

The [Pulse Handbook](https://pulse.ifthis.app/docs) covers installation, manual interval choices, editing workflows, drive and request states, mount/Jolt/Eject, Mac sleep, thermal protection, licensing, troubleshooting, and updates.

## Install

Requires **macOS 14 or later** and an **Apple Silicon Mac**.

1. Download [`Pulse 1.3.1 (build 23)`](https://github.com/artseabra/glitch-os-public/releases/download/v1.3.1/Pulse.dmg).
2. Open the DMG and drag `Pulse.app` to `/Applications`.
3. Launch Pulse — look for the icon in your menu bar (no Dock icon).
4. Turn on the external drives you want mounted and receiving heartbeat activity.

## Updates

The Direct edition includes **Settings → General → Check for Updates…**. Optional daily checks are **Off initially**. Sparkle verifies the signed update feed and downloads. Automatic downloading and silent installation are disabled. Pulse asks before quitting to install, and pending drive requests must settle first. If a staged update defers quitting, wait for pending work to settle, retry Quit and respond to the update prompt. Choosing Later defers installation; it does not cancel the staged update. Confirm that Pulse has exited before assuming it has stopped. Checking for an update does not stop heartbeat activity or require a license.

**If you use 1.2.2 or earlier, download 1.3.1 once**, quit Pulse, and replace `/Applications/Pulse.app` using the DMG. Older versions do not contain this updater. Existing preferences and licenses continue to apply. Future releases can be checked inside Pulse.

## Distribution
- Signed with Developer ID Application + hardened runtime
- Notarized via Apple, stapled, Gatekeeper-accepted
- The Mac app sends no usage analytics or drive activity telemetry; Polar handles licensing
- Direct update checks and downloads use HTTPS through Sparkle; system-profile reporting is disabled

## Verifying a release
```bash
xcrun stapler validate Pulse.dmg
spctl --assess --type open --context context:primary-signature -v Pulse.dmg
```

## Releases
See the [1.3.1 release notes](https://github.com/artseabra/glitch-os-public/releases/tag/v1.3.1) or the [Releases tab](https://github.com/artseabra/glitch-os-public/releases) for downloadable DMGs.
