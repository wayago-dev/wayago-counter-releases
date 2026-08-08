# Changelog

All notable WAYAGO COUNTER changes are documented here in English. Versions follow Semantic Versioning.

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
