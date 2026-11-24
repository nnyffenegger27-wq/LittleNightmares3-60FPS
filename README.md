# Little Nightmares III – 60 FPS patch (Switch, v1.2.1)

Unlocks Little Nightmares III on Nintendo Switch from 30 FPS to 60 FPS.

| | |
|---|---|
| Title ID | `010066101A55A000` |
| Game version | **1.2.1** only |
| `main` build ID | `BB02917589CFB448460E1DDAC4C52828` |
| Tested on | Eden v0.2.1 (PC emulator): stable 60 FPS |
| Real Switch hardware | **untested** (the base console will likely not hold 60 FPS) |

## How it works

On Switch, the game sets the NVN window *present interval* to 2, which shows a frame every other vsync and gives 30 FPS. The interval is computed at `main+0x32D148` (`csinc w22, w9, wzr, ge`). The patch replaces that instruction with `mov w22, #1` (`36 00 80 52`), so the game presents on every vsync (60 FPS).

Unreal Engine scales gameplay with frame time, so the game speed should not change.

## Installation

### Eden / yuzu-based emulators
Copy the `eden/60 FPS` folder to the game's mod folder:
`%APPDATA%\eden\load\010066101A55A000\60 FPS\exefs\main.pchtxt`
(right-click the game → *Open Mod Data Location*). Disable it in *Configure Game → Add-Ons*.

### Atmosphère (real Switch, untested)
Copy `atmosphere/exefs_patches/LN3-60FPS/` to the root of the SD card.

## Notes
- This is a 60 FPS cap, not an uncapped frame rate. It needs a 60 Hz or faster display.
- Only for v1.2.1: other versions have a different build ID and the patch will not apply.
- No game files are included or modified. The patch only contains a 4-byte change.
