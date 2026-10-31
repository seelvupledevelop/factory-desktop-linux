# Factory Desktop 1.1.0 — unofficial Linux port

Unofficial Linux packaging (`.deb` + AppImage) of **Factory Desktop 1.1.0**, built
from the official macOS DMG fetched from Factory's desktop endpoint. Not
affiliated with or supported by Factory — the only official source is
[factory.ai](https://factory.ai).

## Install

### Debian, Ubuntu, Mint, Pop!_OS

```bash
sudo apt install ./factory-desktop_1.1.0_amd64.deb
```

### AppImage

```bash
chmod +x Factory-1.1.0.AppImage
./Factory-1.1.0.AppImage
```

## Verify

```bash
sha256sum -c checksums.txt
```

## What this build does

- Built from the official 1.1.0 x64 DMG (archive-root `Factory.app` layout).
- Linux daemon-transport and system-`droid` adoption patches applied; the
  package bundles no droid binary and uses the `droid` CLI already installed on
  the machine.
- `factory-desktop://` scheme handler registered, so browser sign-in completes
  and hands the callback back to the app.

## Verified

- `dpkg-deb --info` reports `Version: 1.1.0`, `Architecture: amd64`;
  `sha256sum -c checksums.txt` passes.
- Startup tracker reports `outcome: "healthy"` (~3.5 s), with the daemon up and
  `factory-daemon ok` on `127.0.0.1:37643`.
- Runs on Linux Mint 22.3 (x64).

Desktop 1.1.0 matches the current `droid` CLI 1.1.0 model catalog, so the
`Unknown model` / HTTP 400 failure seen when the desktop is newer than the local
CLI no longer occurs.

## Compatibility

Tested on Linux Mint 22.3 (Ubuntu 24.04 base), x64. Fedora/RHEL packages are
not part of this build; use the AppImage there.
