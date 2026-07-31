# Input Glass

[简体中文](README.zh-CN.md)

<p align="center">
  <img src="assets/InputGlass-icon.png" width="160" alt="Input Glass icon">
</p>

Input Glass is a lightweight, always-on-top input-state overlay for Windows and macOS. It displays the live English, Chinese, or Caps Lock state using a draggable Liquid Glass panel.

## Features

- Blue **EN** for English input.
- Red **中** for Chinese input.
- Green **A** while Caps Lock is active.
- Reads the foreground control's real IME state on Windows, including Microsoft Pinyin's `Shift` mode switch.
- Draggable, always on top, and non-blocking for other applications.
- Mouse-wheel scaling from 62% to a safe maximum of 125%.
- Animated colored badge plus a slower environmental Liquid Glass background.
- Remembers window position and scale.
- Custom multi-resolution application icon.
- No network access, telemetry, or account required.

## Requirements

- Python 3.10 or newer.
- Windows 10/11 or a recent macOS release.
- Tkinter, normally included with the official Python installer.

## Run from source

```bash
python -m pip install -r requirements.txt
python main.py
```

## Controls

- Drag anywhere on the panel to move it.
- Scroll the mouse wheel over the panel to resize it.
- Click the small `×` button in the top-right corner to quit.

Settings are stored in `%APPDATA%\InputGlass\settings.json` on Windows and `~/Library/Application Support/InputGlass/settings.json` on macOS.

## Build for Windows

Install the build dependencies, then run the PowerShell build script:

```powershell
python -m pip install -r requirements-build.txt
powershell -ExecutionPolicy Bypass -File .\build_windows.ps1
```

The executable is written to `dist\InputGlass.exe`. If a `D:` drive exists, intermediate build files default to `D:\InputGlassBuild`; override this with `INPUTGLASS_BUILD_ROOT` when needed. Advanced users can redirect the final artifact with `INPUTGLASS_DIST_DIR`.

## Build for macOS

Build the macOS app on macOS itself:

```bash
python3 -m pip install -r requirements-build.txt
chmod +x build_macos.sh
./build_macos.sh
```

The application bundle is written to `dist/InputGlass.app`. Distribution outside your own Mac may require Apple code signing and notarization.

## Project structure

```text
InputGlass/
├─ .github/workflows/build.yml
├─ assets/
│  ├─ InputGlass.ico
│  └─ InputGlass-icon.png
├─ tools/generate_icon.py
├─ main.py
├─ build_windows.ps1
├─ build_macos.sh
├─ requirements.txt
├─ requirements-build.txt
├─ README.md
└─ README.zh-CN.md
```

## Privacy

Input Glass only reads local keyboard, Caps Lock, foreground-window, and IME state. It does not send data over the network.

## Version

This source package corresponds to Input Glass V9 (`9.0.0`).

No license has been selected for this repository. Add a license before inviting third-party reuse or contributions.
