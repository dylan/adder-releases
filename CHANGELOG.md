# Changelog

All notable changes to the Adder language and the Adder Lab & Guide workbench.

## Lab & Guide v0.5.6 · Language v0.8.3 (2026-10-20)

### Changed

- **No source file length cap**: Removed the 65,535-character limit on `.adder` source text so multi-file and heavily commented projects can grow as long as needed while only the compiled `.prg` binary is checked against Commodore 64 memory.
- **Streamlined Language Reference**: Replaced BNF grammar notation boxes and the separate Grammar Summary chapter with direct examples and keyword/operator tables in the Language Reference.

## Lab & Guide v0.5.5 · Language v0.8.2 (2026-10-20)

### Added

- **Ready-to-share disks and cartridges**: Download projects as PRG, D64, D71, D81, or auto-booting Magic Desk and EasyFlash cartridges from the Lab or command line. Companion data travels with the program, and disk exports no longer need an extra host tool.
- **Working files in the Lab**: Programs can load, save, copy, and append file bytes on virtual drives 8–11. Bounded streams work on a C64 too, and cartridge programs can read their bundled assets directly from ROM banks. Snapshots retain mounted disks and open files; reloading the same Lab project keeps its saved files.

## Lab & Guide v0.5.4 · Language v0.8.1 (2026-10-20)

### Added

- **Standalone `adder` command-line tool**: Create new Adder projects from the terminal with `adder new` (picking from Sprite & Sound, Text & Input, Bitmap Canvas, or Minimal starter templates), and compile, inspect cycle and byte costs, and format `.adder` projects directly with `adder compile`, `adder costs`, and `adder format`.

## Lab & Guide v0.5.3 · Language v0.8.1 (2026-10-20)

### Changed

- **Smaller line-drawing `.prg` downloads**: Programs that draw lines and shapes on a canvas (like `Mystify`) no longer bundle empty working memory inside the `.prg` file, shrinking `mystify.prg` by over 11 KB (-90%) with the same per-frame speed.
- **Smaller tile-map and art `.prg` files**: Large tile maps, custom character sets, and sprites are now packed automatically at compile time and unpacked during startup before the first frame appears, saving over 6.6 KB on scrolling games like `Scroller` and `Walker`.
- **Faster 5-digit number formatting (`.digits(5)`)**: Formatting 16-bit scores and counters with `.digits(5)` now uses the fast lookup-table path, saving 350–850 cycles per call so HUD updates leave more frame time for your game.
- **Faster, smaller `Disk.save` and `Disk.load` files**: Saved game data now compacts empty string space, `nil` optionals, and zero-filled arrays over the disk cable while checking file integrity on load, cutting 1541 save sizes and transfer times by 40%–85% on sparse state.

## Lab & Guide v0.5.2 · Language v0.8.0 (2026-10-20)

### Added

- **Delete saved browser projects**: Added a delete button next to each project under `Saved in this browser` in the Lab `Project` menu so you can remove old browser drafts in one click.

## Lab & Guide v0.5.1 · Language v0.8.0 (2026-10-19)

### Added

- **Automatic source formatter**: Format `.adder` files with consistent 2-space indentation, clean spacing, and aligned data table rows while keeping all comments and inline assembly blocks intact.
- **Editor line wrapping and formatting**: Added a `Wrap` toggle in the editor so long lines wrap cleanly while keeping right-hand cycle costs aligned, a `Format` button (`Shift+Alt+F`) in the toolbar, and automatic indentation on `Enter`.
- **Simpler `System.screen.text` strings and characters**: Write `String<N>`, character arrays (like `score.digits(5)`), single `Char` values, and 1-character string literals (`"A"`) directly to `System.screen.text`, and mix `.digits(N)` directly into `if`/`match` choices, `++`, and string interpolation.
- **Standardized project entry points (`project.json`)**: Multi-file folder projects can declare their main file in `project.json` (`"entry"`), or fall back automatically to `main.adder`.
- **Guided `Learn Adder` chapters**: Organized the built-in `Learn Adder` examples into four step-by-step chapters in the project picker, keeping the file tree tucked away for single-file examples and opening it automatically for multi-file projects.

### Changed

- **Clearer starter examples**: Reworked early `Learn Adder` programs so the main concept appears right at the top of the file without extra setup noise.

## Lab & Guide v0.4.2 · Language v0.7.0 (2026-10-19)

### Added

- **Compile-time `const` cooking**: Pure functions with local variables, `for` loops, `if`, and `match` statements—plus `.map` over constant ranges—can now run at compile time inside `const` declarations (such as `isqrt(0..<256)` or `Charset(glyph_fn(0..<256))`), baking lookup tables and custom character sets straight into your `.prg` with zero runtime CPU cost.

### Changed

- **Desktop window controls**: Made window title bars and close boxes easier to grab and added full Port 2 joystick cursor and window dragging alongside 1351 mouse support.

## Lab & Guide v0.4.1 · Language v0.6.0 (2026-10-18)

### Added

- **Bounded strings (`String<N>`)**: Fixed-capacity ASCII strings with `{...}` interpolation, `++` concatenation, fast slices and trimming, character editing, number formatting and parsing, and live display through `Text` and `TextPage`.
- **Typed higher-order functions**: Functions can accept and return other functions (such as `fn(Digit): Digit`), and list `.map` and `.filter` work with both named functions and inline closures.
- **In-place `mut` parameters**: Pass variables, struct fields, and list items with `mut` so helper functions can update caller state in place without copying, while automatically refreshing any screen bindings that depend on them.
- **Background work progress**: Long-running background `work` jobs can report live status with `publish value`, giving your main loop a clean `.progress` snapshot each frame alongside `.running`.
- **Richer `when` cases and interrupts**: Mode `case` blocks can own their own screen bindings, placed views, queues, background jobs, and scroll settings that clean up automatically when switching modes. Raster and timer interrupts now support local variables, control flow, helper calls, and inline `asm` with full cycle budget checks.
- **New String & callback examples**: Added complete greeting, command parser, high-score, and calculator projects, plus an interactive digit-transform example in the Guide.
- **Editor & Guide assistance**: Added autocomplete, hover info, signature help, and line cost breakdowns for `String<N>`, function values, `mut` parameters (showing which variables a call modifies in hover and source costs), `publish value` progress, and interrupts.

### Changed

- **Faster `.map`, `.filter`, and string comparisons**: Inlined known callbacks inside `.map` and `.filter` (including hardware sprite loops) and sped up short string and slice comparisons.
- **Faster `match` dispatch and division**: Compiled dense numeric `match` blocks into fast jump tables, used lookup tables for constant division, prioritized hot loop variables in zero-page memory, and reduced startup and idle costs for full-screen tile maps.
- **Updated learning examples**: Simplified `Flares` with `flares.map(flare_sprite)`, updated Desktop windows to reorder in place with `raise(mut wins, p)`, and updated the nav computer example to count primes in a background job with a live progress bar.
- **Clearer Sound & Atlas Studio guides**: Expanded the Language Reference for `Envelope` and `Tone`, and simplified tile-size and zoom controls in Atlas Studio.

### Fixed

- **Tear-free background `.progress` reads**: Multi-byte `.progress` and `String<N>` snapshots stay consistent across frames even when raster or timer interrupts read them, and reset cleanly when re-entering a mode.
- **Submitted keyboard spaces**: Preserved trailing spaces and exact line lengths when reading submitted keyboard input lines.
- **Smoother mouse & paddle tracking**: Improved 1351 mouse and paddle sampling in the emulator for steadier cursor movement without startup jumps.

## Lab & Guide v0.2.0 · Language v0.3.0 (2026-10-17)

### Added

- **Full SID synthesis & VIC-II sprite controls**: Added `.pulse` and combined SID waveforms, full `Tone` controls (`detune`, `frequency`, `hz`, `pulse_width`, `ring`, `sync`, `gate`, `test`, `filtered`, and ADSR envelopes), chip-wide `Filter` and `volume`, Voice 3 `oscillator` / `envelope` readouts, and VIC-II sprite expansion, priority, multicolor, and collision flags.
- **Built-in game collections**: Added fixed-capacity `Pool` (for active bullets, enemies, and particles), `Ring` queues, shuffled `Deck`, `Rect` hitboxes, frame `Cooldown` timers, `Wave` lookup tables, and compact `Flags` bitsets.
- **Disk saves & file streams**: Added reactive `load` and `save` jobs on `System.drive[8...11]`, streaming `file(name).read(capacity:)`, clear disk error handling, and multi-disk `.d64` exports.
- **Canvas lines, paths, and circles**: Draw lines, connected paths, and exact midpoint circles on hires and multicolor canvases with automatic background restore and `.inverted` overlays.
- **In-app Changelog**: Added a **Changelog** button in the Lab toolbar and a **Changelog** tab inside the Welcome dialog.

### Changed

- **Consistent `color` and `background` names**: Standardized on `color` for foregrounds, cursors, and palettes, and `background` for canvas backgrounds across hires and multicolor modes.
- **Expanded learning examples**: Updated `Engine Room`, `Jupiter Lander`, `Deck Patrol`, and `Crew Console` to demonstrate SID filtering, `Rect.overlaps` hitboxes, `Pool` + `Cooldown` particle sparks, and windowed drawing.
- **Clearer multi-file `entry` badge**: Replaced the dot indicator (`●`) in editor tabs and the file tree with an explicit `entry` badge shown only on multi-file projects.

## Lab & Guide v0.1.3 · Language v0.1.0 (2026-10-17)

### Changed

- **Faster, smaller Desktop example**: Combined the Desktop (`Crew Console`) window borders, interior tiles, and mouse cursor into a single sprite/tile sheet, cutting compiled size to 2,211 bytes and worst-case frame time to 5,204 cycles.

### Fixed

- **Asset Studio code snippets**: Tile entries now copy ready-to-use `Picture(...)` declarations directly and default new layers to the entry's chosen color.

## Lab & Guide v0.1.2 · Language v0.1.0 (2026-10-17)

### Added

- **Atlas & Charset Studio drawing tools**: Added Pencil, Line, Rectangle, Flood Fill, Select/Move, Shift/Wrap, Horizontal/Vertical Flip, Clear, Undo/Redo, neighboring tile previews with click-to-switch, and saved zoom/tool state across tab switches.

## Lab & Guide v0.1.1 · Language v0.1.0 (2026-10-17)

### Added

- **Browser Lab & Guide launch**: Launched the browser Lab workbench and Guide at `https://lab.adder.run/` and linked `Open the Lab` from `https://adder.run/`.

### Changed

- **Refreshed learning-path artwork**: Polished sprites, character sets, and project descriptions across the built-in examples.

## Lab & Guide v0.1.0 · Language v0.1.0 (2026-10-16)

### Added

- **Version display**: Added Language and Lab & Guide version numbers across the CLI (`--version`), Lab toolbar, Welcome dialog, and Quickstart & Reference guides.
- **Welcome splash dialog**: Added the Welcome dialog with emulator loading status, project quick-start steps, and release notes.
