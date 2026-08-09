# Changelog

All notable WAYAGO COUNTER changes are documented here in English. Versions follow Semantic Versioning.

## [0.4.1] - 2026-08-09

### Fixed

- Valid one-device licenses now renew normally after a signed mod update even when the same network previously exhausted the denied-key budget.
- Activation, manual checks and heartbeats share one in-flight request guard and a retry cooldown, preventing accidental request floods.
- Rate-limited responses now show `TOO MANY REQUESTS` instead of the misleading `SERVER UNAVAILABLE` state.

### Diagnostics

- License failures log only the request type, HTTP status and public error code. Keys, device secrets and full HWIDs remain excluded.

## [0.4.0] - 2026-08-09

### Added

- Added a standalone automatic level renderer powered by the Geode FFmpeg API v2 event bridge.
- Added a dedicated `RENDER` action and live video, audio and finalization states to the WAYAGO interface.
- Added an automatic profile that preserves the display aspect ratio and selects resolution, frame rate, bitrate and a compatible hardware or software encoder from the current system.
- Added a second deterministic replay pass through FMOD's WAV writer, followed by automatic MP4 audio muxing.
- Added a configurable render output folder, defaulting to `Geometry Dash/renders`.

### Rendering

- Every exported frame includes the normal WAYAGO playback overlay, frame-window counters, timing circles, CPS, precision and watermark according to the current overlay filters.
- Rendering starts from a clean frame-zero reset with the macro seed restored and ends only when the level completes.
- The renderer is independent from XDBot at runtime; XDBot remains only a recommended GDR/GDR2 file source.
- The bounded encoder queue blocks deterministic capture instead of dropping frames when the encoder is slower than the game.

### Safety

- A dead or divergent replay aborts the render instead of exporting a misleading route.
- Encoder, OpenGL and audio-pass failures stop cleanly, restore FMOD output and preserve a video-only MP4 when audio muxing alone is unavailable.
- FFmpeg binaries remain in the separately maintained FFmpeg API dependency and are not duplicated inside the WAYAGO package.

## [0.3.6] - 2026-08-08

### Fixed

- Replaced runtime MP3 effects with trimmed, preloaded PCM WAV resources, removing the codec's approximately 41 ms leading silence.
- Timing alerts now start on a dedicated FMOD channel, explicitly recover from a paused shared SFX group, and fall back to Geometry Dash's native effect path when direct playback is unavailable.
- Added one-time channel diagnostics and a clear warning when Geometry Dash's global SFX volume is muted.

### Improved

- Raised the minimum alert gain so 7-10 frame timing sounds remain audible over level music while preserving stronger alerts for narrow windows.
- Added a two-physics-tick collision tail after continuous-mode control cycles and cube/robot landings, catching boundary hazards that report death just after the nominal causal segment ends.

## [0.3.5] - 2026-08-08

### Performance

- Replaced two full-from-start boundary confirmations per input with a short baseline certification of the restored private checkpoint.
- Certified checkpoints are reused through their verified causal horizon, so normal offset scans resume close to the tested input instead of replaying the level from frame zero.
- Reduced the default checkpoint spacing from 30 to 18 frames, reduced the guarded input radius from 10 to 4 frames, and raised the default fixed-step analysis speed from 48x to 64x.

### Safety

- Checkpoint certification compares position, velocity, gravity, mode, orientation and grounded state against the original vanilla baseline on every frame.
- A checkpoint that drifts, dies early or restores an invalid state is discarded automatically and the analyzer retries from an earlier snapshot, falling back to frame zero only when no certified snapshot remains.

## [0.3.4] - 2026-08-08

### Fixed

- Corrected the v0.3.3 regression that reduced valid multi-frame ship and wave timings to isolated 1-2 frame results.
- Continuous-mode offsets now start with an isolated test and fall back to a coordinated adjacent-edge repair only after a real death.
- A repaired offset must survive the complete causal control cycle before it can extend the measured window, preventing the short-horizon false passes seen before v0.3.3.

### Diagnostics

- Analysis logs now identify isolated, forward-pair and backward-pair runs and record exactly which full-cycle repair extended a window.

## [0.3.3] - 2026-08-08

### Fixed

- Frame-window boundaries now shift exactly one input edge, preventing adjacent-edge compensation from inflating real 1-4 frame ship and wave windows into 6-10 frame results.
- Ship, wave and swing offsets are validated through the next equivalent edge, covering the complete press-release control cycle and catching late collisions in the same corridor.
- Every checkpoint-derived failure boundary is confirmed by a clean full replay, regardless of the provisional window size.

### Changed

- Alternative full-route candidates remain a separate post-analysis result and can no longer redefine or enlarge an input's measured window.

## [0.3.2] - 2026-08-08

### Changed

- Replaced the generated procedural timing tones with the exact original eight-file MP3 sound pack.
- Packaged every timing sound directly inside the `.geode` release, so no separate download or setup is required.
- Kept startup preloading for the bundled MP3 files to avoid first-use file loading latency.

## [0.3.1] - 2026-08-08

### Fixed

- Backward coordinated input tests now select checkpoints before the earliest changed event instead of the current input.
- Expected trajectory changes after a paired previous release are no longer reported as pre-input replay drift.
- Deaths during backward-pair validation are classified against the complete mutation boundary, preventing analysis from aborting on valid macros.

## [0.3.0] - 2026-08-08

### Added

- Coordinated adjacent-edge route search for ship, wave, swing and robot inputs.
- Mega Hack Replay JSON (`.mhr.json`) and binary (`.mhr`) compatibility import.
- Silicate v3 (`.slc`) compatibility import in the unified macro library.
- Built-in procedural timing sounds for every displayed 0-10 frame bucket.
- Macro compatibility guidance with per-bot recording requirements.

### Improved

- Narrow windows now test isolated and viable neighboring timing patterns before remaining classified as one frame.
- Built-in sounds are generated once and preloaded during mod initialization to remove first-use latency.
- The pause menu and macro library use a compact information hierarchy and clearly label experimental formats.
- Alternative routes are exported without stale window measurements and require a fresh analysis.

### Fixed

- Removed the misleading warning notification shown when optional route candidates were rejected after a successful analysis.
- Preserved clean-reset boundary confirmation while adding coordinated route checks.
- Allowed supported compatibility-import projects to restore from Counter autosave.

### Compatibility

- XDBot GDR/GDR2 remains the recommended and most thoroughly tested workflow.
- Mega Hack MHR and Silicate v3 support is experimental and has not been tested as thoroughly as XDBot.
