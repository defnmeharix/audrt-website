# audrt-website

# AUDRT

A VST3 audio plugin for macOS, built with JUCE 8 and C++. Formerly developed under the name **VocalClean**.

> **Status:** Working VST3 build, tested in Ableton Live 12 on macOS.

<img width="518" height="438" alt="Screenshot 2026-11-07 at 5 43 27 PM" src="https://github.com/user-attachments/assets/9f29e192-5c65-4be4-a5ed-8bbb5bdac77e" />


## Overview

AUDRT is a vocal-focused audio effect plugin.

## Features

- De-Noise Live Audit
- De- Noise Prerecorded Audio  
- Real time Pitch correction

## Requirements

| Item | Version |
|------|---------|
| macOS | 12 or later (Apple Silicon / Intel, depending on your build target) |
| DAW | Any VST3 host (developed and tested with Ableton Live 12) |
| JUCE | 8.0.13 |
| Xcode | Recent version with command-line tools |

## Installation (prebuilt)

1. Download `AUDRT.vst3` from the [Releases](../../releases) page.
2. Copy it to:
   ```
   ~/Library/Audio/Plug-Ins/VST3/
   ```
3. Because the plugin is not code-signed or notarized, macOS may quarantine it. Clear the flag:
   ```bash
   xattr -cr ~/Library/Audio/Plug-Ins/VST3/AUDRT.vst3
   ```
4. Open Ableton Live, go to **Preferences > Plug-Ins**, and enable **Use VST3 Plug-In System Folders**, then rescan.

## Building from source

1. Download [JUCE 8](https://juce.com/) and note where you extract it.
2. Open the project's `.jucer` file in **Projucer**.
3. Under **Global Paths**, make sure the JUCE modules path points at your JUCE folder.
4. Confirm only **VST3** is enabled as a plugin format.
5. Click **Save and Open in IDE** to generate the Xcode project.
6. In Xcode, select the **AUDRT - VST3** scheme and build (`Cmd+B`).

The built plugin is copied to `~/Library/Audio/Plug-Ins/VST3/` if the copy-after-build option is enabled.

### Known build notes

- **Projucer path casing:** on a case-sensitive setup, Projucer may save the JUCE path in lowercase (`juce`) instead of `JUCE`, which breaks the build. If that happens, fix the path in the `.jucer` file after saving, for example:
  ```bash
  sed -i '' 's#/juce/#/JUCE/#g' AUDRT.jucer
  ```
  Adjust the pattern to match your own path.
- **VST2:** not supported. This project is VST3 only.
- **Code signing:** builds are unsigned (no paid Apple Developer account), so local builds may need the `xattr` step above.

## Usage

<!-- TODO: describe the controls -->

| Control | Description |
|---------|-------------|
| Control 1 | De-Noise |
| Control 2 | Pitch correction intensity |

## Project structure

```
AUDRT/
├── Source/
│   ├── PluginProcessor.cpp / .h   # Audio processing
│   └── PluginEditor.cpp / .h      # UI
├── AUDRT.jucer                    # Projucer project
└── README.md
```

<!-- Adjust to match your actual layout -->

## Roadmap

- [ ] Code signing and notarization
- [ ] AU format
- [ ] Windows build

## Contributing

Issues and pull requests are welcome. For larger changes, please open an issue first to discuss what you would like to change.

## License

<!-- TODO: choose a license. JUCE itself is dual-licensed (AGPLv3 / commercial), so check that your choice is compatible. -->

## Acknowledgements

Built with [JUCE](https://juce.com/).
