# Changelog

All notable changes to the Adder language and the Adder Lab & Guide workbench.

## Lab & Guide v0.5.12 · Language v0.8.13 (2026-10-22)

### Fixed

- **Reliable graphics startup in large projects**: Sprites, fonts and screens now initialize from intact original data and restore their authored contents when you run the program again.

## Lab & Guide v0.5.12 · Language v0.8.12 (2026-10-22)

### Changed

- **Smaller, quicker fixed-point calculations**: Bounded coordinate calculations and small fixed-point products need less code and working memory. The Mandelbrot benchmark shrinks from 2,898 to 2,043 program bytes, and its worst-case frame bound falls from 15,163 to 2,695 cycles.
- **Quicker list results and loops**: Functions that build a list from another list can copy directly and initialize only the cells that survive. Eligible private byte loops keep their counter in a processor register; the 40-cell benchmark's frame bound falls from 2,393 to 2,076 cycles.
- **Less per-frame bookkeeping**: Values written on every frame can skip redundant update tracking while retaining change events, histories, checked arithmetic and device write order.
- **Updated frame-cost examples**: The Guide's oversized-frame messages reflect the smaller generated code.

## Lab & Guide v0.5.11 · Language v0.8.11 (2026-10-21)

### Added

- **Go to Definition, Find References, Rename, Symbol Outline, and Quick Fixes in the Lab**: Jump to any symbol or `include` file with `F12` or `Cmd`/`Ctrl`-Click, see read and write occurrences highlighted automatically as you move the cursor, inspect every reference across project files with `Shift+F12`, rename symbols across single-file and multi-file projects with `F2`, jump to any declaration in the file with `Cmd`/`Ctrl+Shift+O`, and apply compiler-verified quick fixes directly from the error tooltip or with `Cmd`/`Ctrl+.`.

## Lab & Guide v0.5.10 · Language v0.8.11 (2026-10-21)

### Added

- **Language server (`adder lsp --stdio`)**: Use Adder in any editor that supports the Language Server Protocol or embed `@adder/compiler/lsp` and `@adder/compiler/service` in browser and desktop tools, with multi-file diagnostics, compiler-verified quick fixes, completions, hover documentation, signature help, go-to-definition, find-references, rename, document symbols, formatting, and inline cycle and byte cost hints across multi-file projects.
- **Universal VS Code extension (`adder-vscode.vsix`)**: Write, inspect, and run Adder programs in desktop VS Code and in the browser on `vscode.dev` with syntax highlighting, inline cycle and byte cost hints, side-by-side cost and assembly reports, and an embedded Commodore 64 emulator panel with automatic virtual disk mounting and hot-reload on save.

### Changed

- **Shared language intelligence and binding hovers in the Lab**: Hovering over `const`, `var`, and `<-` bindings now shows their resolved type details alongside hardware, callable, and cost summaries.

## Lab & Guide v0.5.9 · Language v0.8.10 (2026-10-21)

### Changed

- **Smaller, faster bounded division in fast code**: Whole-number division can now use a small shared table when the declared range fits. The division-by-320 example drops from 537 to 470 program bytes and from a 2,232-cycle frame bound to 84, with checked arithmetic preserved. Ordinary and small code keep their compact choice.
- **Tighter costs for a copy that runs once**: A simple bounded loop that copies a list and clears its Boolean guard now counts that copy once. Every guard test still counts, generated programs are unchanged, and the Lab and Guide explain the bound.
- **Cheaper typed keyboard input**: Stroke and dropped-input readers now use the same bounded repeat helper as the native line editor. The sample's frame bound falls from 8,992 to 5,163 cycles without changing typing behavior, queue capacity or sampling cadence.
- **Reliable RAM limits for large lists**: The final storage check now includes startup-filled lists and alignment, so programs cannot place ordinary data over I/O addresses. Layouts that fit after placement still compile.
- **Clearer video-standard errors**: The emulator now rejects unsupported video standards with a clear error. An invalid request leaves the running machine and its pending audio unchanged.

## Lab & Guide v0.5.8 · Language v0.8.9 (2026-10-21)

### Changed

- **Visible screens with hardware timers**: Text and bitmap displays now start normally in timer programs, including programs whose raster routines begin inactive.
- **Reliable timer program compilation**: Programs whose final timer code needs private temporary storage now receive separate storage instead of failing the final allocation check. Working-storage figures also match the bytes actually reserved when shared workspace is no longer needed.
- **Cheaper native line input**: The native keyboard editor now uses its bounded repeat loop alongside assembly and interrupts, leaving more of each PAL or NTSC frame available for other work without changing typing behavior.

## Lab & Guide v0.5.8 · Language v0.8.8 (2026-10-21)

### Changed

- **Costs you can read at a glance**: Hover or focus a cycle figure for a short card showing its cycle bound, frame share, program bytes and working storage. Activate it to keep the explanation open in the 6502 inspector, in either Woven or Flow.
- **Clearer descriptions of what calls change**: Cost summaries and source hovers use the names you wrote. Exact fields, ranges and expanded helper details remain available when you need them.
- **More useful cost explanations**: The inspector distinguishes bytes attributed to a line from shared routines and deferred work, and keeps unknown, declared, trusted and loop-turn qualifications visible.

## Lab & Guide v0.5.7 · Language v0.8.7 (2026-10-21)

### Changed

- **Smaller byte-scaled arithmetic**: Multiplying or dividing by 256 and other large powers of two now moves whole bytes directly, making packed coordinate decoding cheaper while retaining checked range failures.
- **Smaller hardware mailbox updates**: Reactive bindings that read fixed elements of a hardware array now check only those elements for changes, saving code, working memory, and update work. Reads of a whole array, a slice, or a changing index retain full-array checks.
- **Clearer text frame limits**: A single text scene with separate placements now reports the cycles it needs and the frame's limit when it is too expensive, without claiming the text overlaps. Text fallback attempts also stop retrying options that are already disabled.
- **Expansion-port mailbox reads and faster project loading**: Writing expansion-port memory (`$DE00–$DFFF`) in the emulator now reads back the stored byte when no cartridge claims the address, and multi-file project loading skips common external build and dependency folders.

## Lab & Guide v0.5.7 · Language v0.8.6 (2026-10-21)

### Added

- **New `Plasma` example in `Learn Adder`**: Added a 60 fps extended-background dithered plasma example (`3. Graphics & Assets`) combining a custom 8-glyph Bayer dither charset, four background colors, per-cell color RAM, and a sprite overlay banner.

### Changed

- **Faster screen and color-RAM loops**: Loops that fill a multi-row window of screen cells and colors now run in a single pass ahead of the raster beam whenever the frame work finishes before the beam reaches the bottom of the window, and indexed table lookups and fixed column offsets compile to direct indexed instructions without extra scratch copies.
- **Less repeated work in loops and helpers**: Some values can stay in processor registers across branches and helper calls, making the generated code smaller and faster.
- **Quicker per-frame calculations**: Small private calculations use less memory and spend less time checking whether to update. Event timing, sound changes, and retained text keep their existing behavior.
- **Fewer record and list copies**: Functions returning a record or list can fill a new local directly, using less working memory and doing less copying.
- **Smaller numeric helpers**: Helpers can use their callers' proven byte values and constants directly. The compiler keeps shared code whenever specializing a helper would cost more.
- **Updated cost guide**: The Guide explains the automatic savings available without adding a `fast` mark.
- **Shared frame clocks**: Repeated frame events with the same interval can share a counter, using less code and working memory while keeping their schedules.
- **Smaller, quicker indexed byte stores**: Loops that write a fixed numeric value into a list avoid copying an address before each write and need less temporary storage. Changing values, captured indexes and existing checks keep their usual behavior.

## Lab & Guide v0.5.7 · Language v0.8.5 (2026-10-21)

### Changed

- **What's new on return visits**: Returning to the Lab after a new release now opens the Welcome dialog directly to the `Changelog` tab whenever there is an unseen release entry, and remembers that you've read it once dismissed.

## Lab & Guide v0.5.6 · Language v0.8.5 (2026-10-20)

### Changed

- **Smaller, faster helpers and primitive wrappers**: Functions keep proven integer bounds through nested calls, avoiding repeated checks and working memory when every caller supplies values that fit. Wider callers keep their safeguards.
- **Quicker row updates through helpers**: Loops can calculate a stable row address once even when user functions update its cells or windows. Nested calls and overlapping copies keep their usual order.
- **Less temporary struct storage**: Private struct fields can use their original values directly, and harmless overwritten field assignments disappear along with unused workspace.
- **Correct snapshots and failure locations in mutable helpers**: Local constants keep the value they captured before a parameter changes, and failed result checks report the helper's result line.
- **Correct values through shared methods**: Methods used with different bounds preserve every call's values, including projected text rows and event counters.

## Lab & Guide v0.5.6 · Language v0.8.4 (2026-10-20)

### Changed

- **Smaller programs using structs**: Repeated method calls on the same sized struct now share compiled code and working memory, reducing program size for text regions, collections, and user-defined structs while preserving their behavior.
- **Correct callback choices from changing helpers**: Struct methods that update a passed variable now return the selected callback correctly across repeated calls.
- **Less working memory and setup for functions**: Unused local values and harmless unused assignments now take no storage or instructions, including word-wrapping workspace in character-only printing. Runtime checks and checked loop counters keep their usual safeguards.
- **Smaller, quicker page updates**: Full-screen text programs now prefer a complete scroll whenever it fits the frame, even when printing only every few frames. Hello World uses a smaller program and presents each scroll in one frame. Row-only presenters also leave out an unused chunk-copy routine.
- **Smaller, faster repeated printing**: Fixed text passed through functions and methods can stay in the program's constant tables. Short lines that always start at the left edge skip unnecessary wrapping work, and loops that fill a stable row calculate its address once. Hello World uses less program and working memory.
- **Method arguments keep their original values**: A read-only method keeps the receiver it acquired before evaluating a later argument that changes the same object.

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
