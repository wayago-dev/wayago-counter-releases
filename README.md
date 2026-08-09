# WAYAGO COUNTER releases

This repository distributes signed Windows builds of the private WAYAGO COUNTER Geode mod. It intentionally contains no source code.

## Installation

1. Install Geometry Dash 2.2081 and Geode 5.8.2 or newer. XDBot is strongly recommended for recording macros.
2. Install `FFmpeg API` v2.0.0 or newer from the Geode index. It is required by the automatic level renderer.
3. Download `wayago.wayago-counter.geode` from the latest release and place it in the Geometry Dash `geode/mods` folder.
4. Restart Geometry Dash, open a level, pause, and press the `W` button.
5. Enter the private license key supplied by the administrator. A key binds to the first Windows computer that activates it.
6. In XDBot, use a GDR/GDR2 macro recorded with Vanilla accuracy, 240 TPS, Frame Offset 0, CBF disabled, and frame fixes disabled. WAYAGO COUNTER ignores frame fixes and analyzes with vanilla physics.

## Macro compatibility

- XDBot GDR/GDR2 is the recommended and most thoroughly tested workflow.
- Mega Hack Replay `.mhr.json` and `.mhr` import is experimental.
- Silicate v3 `.slc` import is experimental.

For every format, record at 240 Hz with vanilla physics, disable CBF and physics corrections, then verify the complete route with `PLAY` before starting `ANALYZE`. Mega Hack and Silicate compatibility has not been tested as thoroughly as XDBot.

The eight-file timing pack is embedded as trimmed, preloaded PCM WAV audio. No separate sound download is required, alerts avoid MP3 encoder delay, and playback works offline.

## Automatic rendering

After analyzing at least one exact frame window, press `RENDER` in the WAYAGO popup. The renderer starts the loaded macro from frame zero and exports the level with the active WAYAGO overlay, counters, circles, CPS, precision and watermark. The default profile is 3840x2160 at 60 FPS and 80 Mbps; resolution, frame rate, bitrate, offline video speed and output folder can be changed in Geode's advanced mod settings.

Rendering uses two deterministic passes: the first captures video faster than real time while retaining independent 240 Hz physics steps, and the second safely records level music, game SFX and WAYAGO timing alerts through FMOD. WAYAGO decodes the FMOD PCM stream internally and sends stereo samples to FFmpeg API, which creates the final MP4 in `Geometry Dash/renders` by default. The renderer is independent from the XDBot runtime.

## In-mod workflow

The pause popup follows one numbered path: `1 IMPORT -> 2 ANALYZE -> 3 PLAY -> 4 RENDER`. `GUIDE` explains the recommended XDBot setup, exact-window policy and render output location. Every input edge is measured independently. Exact 1-10 frame timings are shown; wider easy timings and gameplay-irrelevant inputs are intentionally excluded from circles, sounds, counters and precision.

The in-mod updater accepts only release metadata signed by the WAYAGO license server and verifies the exact package SHA-256 before installation. Release DLLs ship without PDB/COFF symbols, expose only the Geode entry point, protect private protocol literals, and enable Windows CFG, EH continuation, CET, ASLR and DEP metadata.

During PLAY, v0.6.0 can show brief English timing explanations when the same macro's analysis proves a next-edge dependency, a separated alternate alignment, or a hard mode-transition alignment. The measured circle remains the stable contiguous PASS range. These notes never compare frame-window totals from different levels, and CBF/subtick analysis remains disabled.

## Access

The binary is proprietary. A valid one-device license is required for all analysis, playback, macro, and editor functionality. Redistribution, modification, reverse engineering, and bypassing the license system are not permitted.

For device resets or access issues, contact the license administrator.
