# Wino Mail Unlocked — Builder

> ⚠️ **This repository contains NO source code of Wino Mail.**  
> It is a **GitHub Actions CI Builder** that automatically fetches, builds, signs and releases MSIX packages.

## What is this?

This repository uses GitHub Actions to:

1. `git clone --depth=1` from **[FranzFerdiand/Wino-Mail-unlocked](https://github.com/FranzFerdiand/Wino-Mail-unlocked)** (a community fork of Wino Mail that removes the 3-account limit)
2. Patch AppxManifest Publisher to match the self-signed certificate
3. Build and package as a self-signed **MSIX** using MSBuild
4. Create a GitHub Release with the MSIX installer and public certificate `cert.crt`

The upstream fork is based on [bkaankose/Wino-Mail](https://github.com/bkaankose/Wino-Mail) (open source, GPLv3), which has been modified to remove the paid account restriction. **This is fully compliant with the open-source license.**

## Required Secrets

| Secret | Description |
|---|---|
| `SIGN_PFX_B64` | Base64 encoded self-signed `.pfx` certificate |
| `SIGN_PFX_PWD` | Password for the `.pfx` certificate |

## Trigger Methods

- ⏰ Scheduled every Sunday at 06:00 UTC (`cron: 0 6 * * 0`)
- 🖐️ Manual trigger via **Run workflow**

## Installation Guide

1. Download `cert.crt` from Release → Right-click → Install Certificate → **Local Machine** → Place into **Trusted Root Certification Authorities** or **Trusted People**
2. Double-click the `.msix` file → Click **Install**
3. Launch **Wino Mail** from Start Menu

> If installation fails, make sure **Sideload apps** is enabled (Settings → Privacy & security → For developers)

## Notes

> A lot of things are hardcoded in the workflow file, so please **do NOT fork this repository for secondary modification unless necessary**. This builder is already sufficient for its purpose.

## Credits

- Original Wino Mail: [@bkaankose/Wino-Mail](https://github.com/bkaankose/Wino-Mail) — Please consider supporting the original author ❤️
- Unlocked fork: [@FranzFerdiand/Wino-Mail-unlocked](https://github.com/FranzFerdiand/Wino-Mail-unlocked)
