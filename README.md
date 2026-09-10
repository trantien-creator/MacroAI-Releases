<div align="center">

<img src="assets/smartmacroai-logo.png" alt="SmartMacroAI" width="320">

# SmartMacroAI

**Visual automation for Windows applications and Android emulators**

Build, run, and monitor repeatable workflows without writing code.

[![Version](https://img.shields.io/badge/version-v1.3.0--beta.5-0078D4?style=flat-square)](https://github.com/trantien-creator/MacroAI-Releases/releases/tag/v1.3.0-beta.5)
![Platform](https://img.shields.io/badge/platform-Windows%2010%2B-0078D4?style=flat-square&logo=windows)
![Runtime](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet)
![UI](https://img.shields.io/badge/UI-English%20%7C%20Ti%E1%BA%BFng%20Vi%E1%BB%87t-F7931E?style=flat-square)

[Tiếng Việt](README.vi.md)

**[Download Beta 5](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.5/SmartMacroAI-v1.3.0-beta.5-win-x64-Setup.exe)** · **[Get a free beta key](https://cyber-bike-56a.notion.site/SmartMacroAI-License-20-Thi-t-B-30-Ng-y-3d6cdffabe278141a343ea8872c11687)** · **[View demo](#demo)**

[Website](https://smartmacroai.pages.dev/) · [All releases](https://github.com/trantien-creator/MacroAI-Releases/releases)

</div>

> [!WARNING]
> Beta 5 is unsigned. Windows SmartScreen may show a warning. Download only from this official repository and verify the published SHA256 checksum before running the installer.

## What SmartMacroAI does

SmartMacroAI is a desktop visual automation tool for Windows applications and Android emulators.
It combines a workflow editor, recording tools, image matching, OCR, conditions, loops, scheduling, and run diagnostics in one application.
The goal is to make repeatable desktop and emulator tasks easier to build, inspect, and maintain.

## Main benefits

- Build workflows visually with ordered steps and nested branches.
- Automate Windows targets through HWND, input, and optional driver modes.
- Control Android emulators through ADB without occupying the Windows pointer.
- Record and edit click, drag, key, text, wait, scroll, and screenshot actions.
- Use image recognition and OCR to react to visible interface states.
- Reuse variables, CSV data, child workflows, conditions, and loops.
- Monitor execution with logs, step status, breakpoints, pause, and resume.
- Use normalized coordinates for workflows that must adapt to target size changes.

## Demo

<p align="center">
  <img src="assets/product-overview.png" alt="SmartMacroAI product overview" width="820">
</p>

<p align="center">
  <img src="assets/demo-workspace.png" alt="SmartMacroAI workspace demo with neutral sample data" width="1000">
</p>
The screenshot uses neutral demo data and contains no personal workflow names, target titles, local paths, keys, or private logs.

## Visual workflow editor

- Switch between sequential list and graph views.
- Add, rename, enable, disable, duplicate, copy, paste, and reorder steps.
- Model nested Repeat, Try/Catch, If Variable, If Image, and If Text branches.
- Inspect the active step, elapsed time, execution path, and recent trace.
- Lock editing operations while a workflow is running.

## Windows and Android emulator automation

| Target | Typical use | Notes |
|---|---|---|
| Windows/HWND | Desktop application workflows | Background behavior depends on the target application and selected input mode. |
| Raw or hardware input | Applications that reject window messages | May require foreground access and may affect the physical pointer or keyboard. |
| Optional driver mode | Low-level input compatibility | Requires Administrator access, driver installation, and a restart. |
| Android emulator via ADB | Emulator taps, swipes, keys, text, and captures | The selected ADB device must report the `device` state. |

## Beta 5 downloads

| Package | Size | Download |
|---|---:|---|
| Windows x64 installer | 237 MiB | [Setup EXE](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.5/SmartMacroAI-v1.3.0-beta.5-win-x64-Setup.exe) |
| Windows x64 portable | 345 MiB | [ZIP](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.5/SmartMacroAI-v1.3.0-beta.5-win-x64.zip) |
| Checksums | — | [SHA256SUMS.txt](https://github.com/trantien-creator/MacroAI-Releases/releases/download/v1.3.0-beta.5/SHA256SUMS.txt) |


## Verify the download

```powershell
Get-FileHash .\SmartMacroAI-v1.3.0-beta.5-win-x64-Setup.exe -Algorithm SHA256
Get-Content .\SHA256SUMS.txt
```

Compare the calculated value with `SHA256SUMS.txt`.
Do not run the package when the values differ.

## Quick start

1. Download the Beta 5 installer or portable ZIP.
2. Verify its SHA256 checksum.
3. Install or extract SmartMacroAI, then activate it with a valid beta key.
4. Create a workflow or open one of your saved scripts.
5. Select a Windows target or an available ADB emulator.
6. Add or record actions, save the workflow, run it, and review the logs.

## Free beta access

A shared Community beta key is available from the [beta key page](https://cyber-bike-56a.notion.site/SmartMacroAI-License-20-Thi-t-B-30-Ng-y-3d6cdffabe278141a343ea8872c11687).
The page displays the current device and time limits.
Beta access may be changed or withdrawn in a later commercial release.

## Coordinate behavior

Normalized click and drag coordinates are recalculated for the current Windows client area or Android display size.
Pixel coordinates, image-search regions, and OCR regions can still require adjustment when resolution, aspect ratio, orientation, or DPI changes.
Always test a workflow after moving it to a different environment.

## Technical documentation

- [Local HTTP API](docs/HTTP-API.md)
- [Discord Webhook](docs/DISCORD-WEBHOOK.md)
- [OCR](docs/OCR.md)
- [ADB and Android emulators](docs/ADB.md)

## System requirements

- Windows 10 build 19041 or later.
- 64-bit Windows for the current release package.
- Enough free disk space; ADB access is required when automating an Android emulator.
- Administrator access only for optional driver installation.

## Beta limitations

- The installer is not digitally signed.
- Compatibility varies between target applications and input modes.
- Emulator ADB ports and capture behavior vary by vendor.
- Image recognition depends on the target UI, scaling, and template quality.

## Privacy, terms, and license

- [Privacy Policy](PRIVACY.md)
- [Terms of Use and EULA](TERMS.md)
- [Proprietary License](LICENSE)
- [Changelog](CHANGELOG.md)

SmartMacroAI is proprietary software developed by **Trần Tiến**.
Copyright © 2026. All rights reserved.

## Support

- [Open an issue](https://github.com/trantien-creator/MacroAI-Releases/issues)
- Email: `hotrantentien98@gmail.com`
- Website: [smartmacroai.pages.dev](https://smartmacroai.pages.dev/)

This public repository contains product documentation and official release downloads.
It does not contain the private application source code, credentials, license secrets, or user data.
