# WAYAGO COUNTER releases

This repository distributes signed Windows builds of the private WAYAGO COUNTER Geode mod. It intentionally contains no source code.

## Installation

1. Install Geometry Dash 2.2081 and Geode 5.8.2 or newer. XDBot is strongly recommended for recording macros.
2. Download `wayago.wayago-counter.geode` from the latest release and place it in the Geometry Dash `geode/mods` folder.
3. Restart Geometry Dash, open a level, pause, and press the `W` button.
4. Enter the private license key supplied by the administrator. A key binds to the first Windows computer that activates it.
5. In XDBot, use a GDR/GDR2 macro recorded with Vanilla accuracy, 240 TPS, Frame Offset 0, CBF disabled, and frame fixes disabled. WAYAGO COUNTER ignores frame fixes and analyzes with vanilla physics.

## Macro compatibility

- XDBot GDR/GDR2 is the recommended and most thoroughly tested workflow.
- Mega Hack Replay `.mhr.json` and `.mhr` import is experimental.
- Silicate v3 `.slc` import is experimental.

For every format, record at 240 Hz with vanilla physics, disable CBF and physics corrections, then verify the complete route with `PLAY` before starting `ANALYZE`. Mega Hack and Silicate compatibility has not been tested as thoroughly as XDBot.

The eight-file timing pack is embedded as trimmed, preloaded PCM WAV audio. No separate sound download is required, alerts avoid MP3 encoder delay, and playback works offline.

The in-mod updater accepts only release metadata signed by the WAYAGO license server and verifies the exact package SHA-256 before installation. Release DLLs ship without PDB/COFF symbols, expose only the Geode entry point, protect private protocol literals, and enable Windows CFG, EH continuation, CET, ASLR and DEP metadata.

## Access

The binary is proprietary. A valid one-device license is required for all analysis, playback, macro, and editor functionality. Redistribution, modification, reverse engineering, and bypassing the license system are not permitted.

For device resets or access issues, contact the license administrator.
