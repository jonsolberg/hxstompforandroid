# HX Stomp Control

An Android app for the Line 6 HX Stomp, talking to the pedal directly over USB –
a first step towards an HX Edit for Android. Written in Kotlin with Jetpack Compose.

> Independent hobby project, not affiliated with, endorsed by or sponsored by Line 6
> or Yamaha Guitar Group. Line 6, HX Stomp and Helix are trademarks of their owners.

## Status – version 0.1 (experimental)

- Reads the preset list from the pedal and shows it bank by bank (00A–41C)
- Tap a preset to make it active on the pedal
- Search presets by name or number
- USB log (ⓘ) with every packet sent and received – share it when something fails

Works with the **HX Stomp**. The **HX Stomp XL** and **Helix Floor** are recognised too
(same protocol), but untested.

Planned: block on/off, parameter editing, snapshots, renaming, backups.

## Requirements

- Android 8.0 or newer with USB host (OTG) support
- A USB-C to USB-B cable (or an OTG adapter) from the phone to the pedal's USB port

Plug the pedal in and Android offers to open the app; tick *always* to skip the question next time.

## Download

**[Download the latest APK](https://github.com/jonsolberg/hxstompforandroid/releases/latest/download/HXStompControl.apk)**

All versions are under [Releases](https://github.com/jonsolberg/hxstompforandroid/releases).
Every push to `main` builds the APK and publishes it there.

## How it works

The pedal speaks a vendor-specific protocol over USB bulk transfers (the one HX Edit uses).
Each operation opens a short session: drain stale data → 5-packet handshake → command.
Replies are MessagePack. See `app/src/main/java/se/jonsolberg/hxstomp/usb/`.

The protocol description comes from the [OpenHX](https://github.com/allansomensi/openhx)
project's black-box documentation – see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## License

GPL-3.0-or-later – see [LICENSE](LICENSE).
