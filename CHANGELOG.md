# Changelog

All notable changes to the Adder language and the Adder Lab & Guide workbench.

## Lab & Guide v0.5.44 · Language v0.8.40 (2026-10-24)

### Added

- **Writable memory windows**: Give fixed or moving slices and rectangles a name, then edit their backing cells directly. Matching types, mapped memory and case scopes follow the same checked rules.
- **Publish complete values**: Give raster and timer interrupts related settings together with `Publication(initial:)` and `publish(value)`. Readers see a complete earlier or replacement value, and saved snapshots stay unchanged.
- **Prove an early finish**: Add `before(line:)` to a frame handler or native raster interrupt when its complete work must return before a raster line. The compiler checks transfer delays, earlier work and interrupt interference on PAL and both NTSC models, and explains when it cannot prove the boundary. Simple Guide examples show expansion-memory updates and interrupt completion.

## Lab & Guide v0.5.43 · Language v0.8.39 (2026-10-24)

### Added

- **Complete values for interrupt readers**: Share correlated settings with screen and timer interrupts at the moment you publish them. Saved values stay unchanged when newer settings arrive, and the Guide shows how to choose an initial value and publish updates.
- **Compose published updates**: Build a checked replacement with collection functions and pipes, or publish sampled values from a named or inline foreground action. Uncalled actions add no publication work, while failed replacements keep the previous value.

### Fixed

- **Keep device handles out of retained values**: Publications and work progress refuse REU handles instead of treating them as ordinary copied data.
- **Keep published values read-only**: Expansion-memory fetches and swaps cannot overwrite a publication through its current value or a moving window. Copy the value into a variable when you need a mutable destination.
- **Clearer messages**: Read-only checks and interrupt guidance name the calls you write and explain when foreground code can share a replacement.

## Lab & Guide v0.5.42 · Language v0.8.38 (2026-10-24)

### Added

- **Writable named windows**: Name fixed or moving slices and rectangular windows over variables or mapped memory, then edit their selected cells directly. Matching type annotations and case scopes follow the same rules. Simple Guide examples show live windows beside copied variables.

### Fixed

- **Keep rectangle copies within a frame**: Proven in-bounds rectangles retain the same compact row-copy code as an explicit row loop, while uncertain windows keep their full bounds checks.
- **Check the whole rectangle first**: Invalid rectangular windows stop before changing any selected cells, preserving earlier completed work and neighboring memory.
- **Consistent expansion-memory evaluation**: The independent evaluator now applies mapped REU fetches and swaps to the actual mapped memory, matching compiled execution.
- **Restore maintained mapped values**: Active mapped outputs restore their bound values after overlapping handler or expansion-memory writes, including unchanged values and case reentry.

## Lab & Guide v0.5.41 · Language v0.8.37 (2026-10-24)

### Added

- **Read calculations from left to right**: Compose values with either `|>` or `:>`. Fixed-list helpers such as `map`, `filter`, `reduce`, `scan` and `zip_with` work directly or in pipes, with typed callbacks and missing positions preserved.
- **Learn and observe functional pipelines**: The runnable Sensor desk lesson teaches calibration, paired slots, original indexes and seeded totals. Explicit `action` callbacks and whole-value `do` let handlers observe a batch once while its value continues through the pipeline.
- **Check relationships before your program runs**: Use `#assert condition, "explanation"` to catch broken relationships between constants. A failed check points to your source and shows your explanation; a passing check adds no code or memory to the C64 program. Cargo drop now checks that its pod can reach the clamp.
- **Choose bounded slower updates**: Put `#allow frame_skips` at the start of your entry source to permit supported calculations that take several display refreshes. Adder keeps strict timing by default and still refuses unsupported timing services or resource failures. Successful slower builds show a warning and separate bounds for PAL, NTSC and early NTSC in the CLI, Lab and VS Code.

### Changed

- **One collection spelling to learn**: Fixed-list calculations now use standalone functions and explicit pure callbacks. Examples, editor help and the Guide teach this API, while type-specific operations keep their members.
- **Smaller total map chains**: Consecutive maps with proven total numeric callbacks can share intermediate work and storage. Complete-program cost checks preserve required stage boundaries and resource limits.

### Fixed

- **Keep mapped sprites and labels consistent**: Inline, named and piped sprite calculations use the same screen-relative positions. Character lists compose with formatted digits, and actions retain their checked behavior through project includes.
- **Keep sprite positions compact with named limits**: Numeric limits written with constants now keep the same compact coordinate code as literal limits.

## Lab & Guide v0.5.40 · Language v0.8.36 (2026-10-24)

### Added

- **Learn functional composition at the Sensor desk**: A new runnable chapter 2 lesson pairs sensor slots, calibrates readings, preserves missing positions, labels original indexes and folds a total from a seed. SPACE logs one whole batch through `do`, including an empty batch. The Quickstart introduces pipes with a small calculation you can run.

### Fixed

- **Keep mapped sprites in place**: Inline and piped sprite calculations preserve the same screen-relative positions as named functions.
- **Compose character labels with numbers**: `append` now combines character lists with `digits()` results without an unnecessary type error. Actions used through an included project keep the same checked behavior as standalone source.

## Lab & Guide v0.5.39 · Language v0.8.35 (2026-10-24)

### Added

- **Observe a pipeline without changing its value**: Explicit `action` callbacks perform synchronous screen and region services. `do(value, action)` observes the whole value once, including missing readings, then lets it continue through the pipeline. Terminal action pipes finish with no result. The compiler keeps these service effects separate from pure calculations and checks their snapshot lifetimes.

## Lab & Guide v0.5.38 · Language v0.8.34 (2026-10-24)

### Added

- **Compose collection calculations as functions**: Use `map(values, transform)`, `filter(values, predicate)` and reductions directly or in pipes. New helpers combine matching slots, keep original indexes, search, reverse, join and flatten fixed lists. `reduce` starts from your seed; `scan` shows the accumulator after each input slot.
- **Reuse typed collection functions**: A complete function signature can specialize a standard helper for use as a callback. Your own declarations can use the same names.

### Changed

- **Smaller total map chains**: Consecutive maps with proven total numeric callbacks can share intermediate work and storage. Checked stages, missing slots and callback captures retain their required boundaries.
- **One collection spelling to learn**: Fixed-list calculations now use free functions and explicit pure callbacks. Examples, editor help and the Guide use the current API; type-specific operations keep their members. The Guide also explains that `count` counts present slots, including `false`, and filtering preserves gaps.

## Lab & Guide v0.5.37 · Language v0.8.33 (2026-10-24)

### Added

- **Read transformations from left to right**: Pipe a value into a function with `|>` or the Commodore-friendly `:>`. Both spellings pass the value as the first argument, preserve checks and evaluation order, and work with named functions or function values. Formatting and editor help keep the spelling you chose.

## Lab & Guide v0.5.36 · Language v0.8.32 (2026-10-24)

### Changed

- **Lean expansion-memory stores**: Bounded stores from stable mapped RAM can avoid temporary copies when the compiler can prove the source stays unchanged. Complete memory, startup and frame costs still decide whether the shortcut is used.
- **Smaller, faster text programs**: Some text programs now place character maps more efficiently. Checked character bounds and complete-program cost checks preserve initialization and retain the ordinary layout whenever it is the better choice.

### Fixed

- **Fill expansion memory from complete projects**: REU fills now compile through the CLI and project API as they do from standalone source, preserving argument order, capacity checks and DMA accounting.

## Lab & Guide v0.5.35 · Language v0.8.31 (2026-10-23)

### Fixed

- **More stable Ultimate settings on iPhone**: The address dialog now sits outside the workspace that moves when the keyboard opens, so its input can stay in place while you enter an address.
- **No late welcome interruption**: If you start typing or using the Lab while its welcome information loads, the welcome screen waits for you to open it instead of stealing focus.

## Lab & Guide v0.5.34 · Language v0.8.31 (2026-10-23)

### Fixed

- **Steady address entry on phones**: The Ultimate IP address field keeps focus when the on-screen keyboard opens or resizes. Search fields in the top-bar menus stay usable too.

## Lab & Guide v0.5.33 · Language v0.8.31 (2026-10-23)

### Changed

- **Keep editing while the Lab is busy**: Long compiles, C64 startup, language help, image work and project saves run in the background, so they no longer freeze the editor or its controls.
- **Open large projects more smoothly**: The Lab loads optional panels when needed, reuses unchanged project files and displays long code listings a screenful at a time.

### Fixed

- **Start sound when you choose**: Enable sound from the C64 controls. Typing and Run no longer open an audio device, and unavailable sound can be retried while the program keeps running silently.
- **Keep the latest image edits**: Run, Save, downloads and project switching wait for accepted image edits. The Lab warns before leaving with work that has not reached storage, and explains how to retry interrupted background work.
- **Keep virtual disk changes when choosing memory hardware**: Applying REU settings preserves files already saved to the mounted disk.

## Lab & Guide v0.5.32 · Language v0.8.31 (2026-10-23)

### Added

- **Choose your emulated REU**: Lab and VS Code let you select 128 KiB through 16 MiB, choose Commodore or Ultimate behavior, and load an optional expansion image. Lab groups these choices in one dialog with image-size checks and a single Apply and restart action. Changing hardware retains mounted disks; the stock C64 remains the default.

## Lab & Guide v0.5.31 · Language v0.8.31 (2026-10-23)

### Added

- **Use REU storage from Adder**: Check for a RAM expansion unit and its capacity, then store, fetch, swap, verify or fill bounded byte windows. Transfers preserve logical addresses across bank boundaries and include DMA time in the frame budget. The Guide includes a complete example and explains the path for machines without enough expansion memory.

## Lab & Guide v0.5.30 · Language v0.8.30 (2026-10-23)

### Added

- **Emulate RAM expansion hardware**: Hosts can attach an REU with 128 KiB through 16 MiB of storage, preload an image, and choose Commodore, Ultimate or Ultimate extended behavior. Transfers share machine time with the display and timers, and snapshots retain the expansion's data and controls.

### Fixed

- **More accurate sprite timing on NTSC machines**: Sprite transfers now use the correct bus slots across the end of a scanline. REU transfers also preserve the CPU's granted bus access when a display pause ends.

## Lab & Guide v0.5.30 · Language v0.8.29 (2026-10-23)

### Added

- **Share compiled Adder libraries (WIP)**: Build one `.addl` file and import its functions into another Adder project. The compiler checks calls and arranges memory, addresses and initialization for you. Libraries currently support stateless functions that take one or two byte values and return a byte.
- **See what a library offers**: Inspect its functions and requirements with the Adder CLI, or browse its interface in the Lab. Editor completions, signatures and hovers use the same interface and refresh when the library changes.
- **Try a complete library project**: The new Compiled Math Lab example calls a shared library and shows the results. The Guide walks through building, inspecting and using a library with the installed CLI, with a separate example for assembly callers.

## Lab & Guide v0.5.29 · Language v0.8.28 (2026-10-23)

### Added

- **Use Adder functions from other C64 programs (WIP)**: Export stateless functions that take one or two byte values and return a byte. Adder checks for possible failures, builds the library at the memory addresses you choose, and supplies the call addresses and memory, stack and cycle costs. The Guide includes a complete assembly caller.

### Changed

- **Faster builds while you work**: The Lab can reuse recent successful builds when you return to a project or undo an edit. Edited programs still get checked. Adder also skips loop searches that cannot help, and compiler integrations can keep their own build caches.
- **Smaller, faster loops**: Some short loops that mark or move array entries now need less setup. Adder chooses the shortcut when the whole program gets smaller and quicker within its memory and timing limits.
- **Smaller game messages**: Adder can share more code between repeated message endings. Snake saves another 16 bytes with the same startup, message and frame costs.

### Fixed

- **Build libraries with the Adder CLI**: The Guide now uses installed `adder` commands and local files for its library and assembly caller. It also explains how to copy the generated bindings and load both programs.

## Lab & Guide v0.5.26 · Language v0.8.23 (2026-10-22)

### Changed

- **Smaller repeated game messages**: Some repeated message endings now take less program space while keeping the same memory, startup and frame limits. Snake saves 72 bytes without slowing its splash or other message paths. Source costs still include all the work a message executes.

## Lab & Guide v0.5.26 · Language v0.8.22 (2026-10-22)

### Changed

- **Lighter guarded loops**: Short loops that mark or shift array entries can now count their turns in a CPU register. Adder selects this when the whole program improves without extra memory or startup work.

## Lab & Guide v0.5.26 · Language v0.8.21 (2026-10-22)

### Changed

- **Smaller wrapping updates**: Some bounded counters now skip a temporary reload after wrapping, making the update smaller and faster while keeping the same values and checks.

## Lab & Guide v0.5.26 · Language v0.8.20 (2026-10-22)

### Changed

- **Split C64 keyboard and joystick deck**: The C64 screen panel now includes a toggleable on-screen control deck (open by default on touch screens) with a cross D-pad and hold-latch mode for Joystick 2, dedicated `FIRE`, `RUN/STOP`, `RESTORE`, `DEL`/`INST`, `HOME`/`CLR`, `SPACE` and `RETURN` keys, sticky `SHIFT`, `C=` and `CTRL` modifiers, and a key bank covering `A–Z`, numbers and symbols (including `↑`/`π` and `←`), `F1–F8` and cursor keys. The redundant compile-details disclosure under the C64 screen has been removed so the screen and controls fit cleanly on mobile and desktop.

## Lab & Guide v0.5.25 · Language v0.8.20 (2026-10-22)

### Changed

- **Free whole-screen color fills with row and slice accents**: Setting a constant base color across `System.screen.color` and then coloring individual rows, columns, or regions now folds the whole-screen fill into the initial screen clear and runs constant slice accents once at start-up instead of redrawing the overlapping rows every frame.

## Lab & Guide v0.5.25 · Language v0.8.19 (2026-10-22)

### Changed

- **Lighter, more accurate C64 CPU emulation**: The built-in 6510 emulator avoids temporary allocations on every instruction and counts clock cycles directly from memory and I/O bus activity. Breakpoint checks no longer copy CPU state on each hit, and disabling interrupts with `sei` during a VIC-II DMA pause now ignores maskable interrupts that arrive only during that pause.

## Lab & Guide v0.5.24 · Language v0.8.19 (2026-10-22)

### Fixed

- **CLI guide links**: Removed an inaccessible repository reference from the command-line guide. Public cost documentation and built-in command help remain available.

## Lab & Guide v0.5.23 · Language v0.8.19 (2026-10-22)

### Changed

- **Faster repeated language help**: VS Code remembers recent source analysis and hint results, refreshing them when files change. Common built-in completions answer directly, and language help runs separately from background checks and builds so those jobs cannot hold up a hint.
- **Assembly stays simple**: The cost pane shows authored assembly directly, without expansion arrows or a second copy underneath. Source links, branch navigation and cost figures stay available.
- **Command-line compiler at a glance**: The Guide now has a short reference for creating projects, compiling programs, reading costs, formatting source and starting the language server. The Quickstart links straight to it, with fuller command help in the tools documentation.

## Lab & Guide v0.5.22 · Language v0.8.19 (2026-10-22)

### Changed

- **Whole-project checks in VS Code**: Files included by a nested project entry now see the project's shared declarations and assembly labels, and load assets from the project folder. Switching files keeps inline costs attached to the right source, including after a cached compile.
- **Costs stay beside your code**: Compact clickable cost hints replace the rows between source lines. The cost pane follows the Lab's Woven layout, with source cost bars and indented instructions, and keeps project totals on a single scrollable strip. Its optional editor-level frame summary starts disabled.
- **Language help while you edit**: Completions, function signatures, hovers and symbol navigation use source checking without loading binary assets or building a program. Available help keeps working with incomplete calls and unavailable assets. Hovering no longer starts cost measurement, and ordinary edits avoid compiling just to find unused fast marks.

- **Clearer loop and byte examples**: The Guide and authoring skill explain bounded loops whose end changes while the program runs, and the skill shows how to read and write the bytes of a number. The splash uses blank-font padding, while Undercrypt builds its character map and visits its rooms with shorter source.

## Lab & Guide v0.5.21 · Language v0.8.16 (2026-10-22)

### Changed

- **Games and demos together in Classics**: Conduit is now called Snake. Find it alongside Jupiter Lander, Mystify and Plasma in Classics, after the learning path. All four remain on the examples disk.

## Lab & Guide v0.5.20 · Language v0.8.16 (2026-10-22)

### Changed

- **Source and assembly together in VS Code**: Clicking a cost opens a dedicated side view attached to that source file, following its cursor. Each file keeps its own cost tab. Expanded source rows lead straight to instruction bytes and cycles. Follow assembly targets and return with Back, switch labels and addresses, or copy the selected assembly. The Lab's frame meter shows where the frame goes and links its busiest stretches back to source. The view updates as you edit, including unsaved changes, and clears obsolete assembly when source needs a correction.

- **A shorter toolbar in narrow windows**: Hot load and every download format move into More when space is tight, keeping the main commands on one row. Phones keep Guide and device actions in the same menu; wide windows retain the visible Hot load and Download controls.

## Lab & Guide v0.5.19 · Language v0.8.16 (2026-10-22)

### Changed

- **Editor controls stay with your source**: Formatting, wrapping, text size and phone cost visibility are available beside the editor, with a local Options menu on phones. About & release notes is now a direct desktop action beside Guide and Ko-fi.
- **A smaller status bar**: Running status and build figures stay on one compact line. Scroll the figures horizontally when the window is narrow, using touch or the keyboard to reach every value.

## Lab & Guide v0.5.18 · Language v0.8.16 (2026-10-22)

### Changed

- **A clearer command shelf**: Guide, Ko-fi and More now sit beside the title on desktop, with Run, Save and device actions below. Send to Ultimate and its settings share one joined control.

### Fixed

- **Single outlines on saved buttons**: Disabled toolbar actions keep one clean border while retaining their larger touch targets.

## Lab & Guide v0.5.17 · Language v0.8.16 (2026-10-22)

### Changed

- **Clearer Lab commands and a bottom status bar**: Project, run, download and help actions stay grouped and visible. Running status and build figures now live beneath the workspace, with a compact Stats control on phones so more room stays available for your program.
- **Easier menus and release notes**: Command menus stay within the window, support keyboard navigation and return focus when closed. Larger hit areas help on touch screens, and About and release history share one destination in More.

## Lab & Guide v0.5.16 · Language v0.8.19 (2026-10-22)

### Changed

- **Smarter storage for record lists**: Adder can now store different kinds of records in different ways to suit how your program uses them. It chooses a new layout when that saves memory or cycles without increasing other program costs.

## Lab & Guide v0.5.16 · Language v0.8.18 (2026-10-22)

### Changed

- **Calculate shared values once**: When consecutive outputs share the same changing state and use the same safe integer calculation, Adder can calculate it once for that update. It uses this shortcut when the whole program gets smaller or faster without extra storage or startup work.

## Lab & Guide v0.5.16 · Language v0.8.17 (2026-10-22)

### Changed

- **Less repeated checking for related outputs**: Consecutive outputs that use the same state can now check for changes together. This works automatically with struct methods and reactive calculations, keeping clock timing and output order intact. Signal Test uses 16 fewer program bytes and has a 20-cycle lower worst-case frame bound.

## Lab & Guide v0.5.16 · Language v0.8.16 (2026-10-22)

### Added

- **Read and write the bytes of a 16-bit number**: Read the low and high bytes of any 2-byte whole-number expression with `.lo` and `.hi` (`Number<u8>`). Write the bytes of a `Number<u16>` variable with `.lo = ...` and `.hi = ...`, without masks or division.
- **Loops with changing upper bounds (`0..<count`)**: Use a changing upper bound in `for` loops over `a..<b` when its integer type has a known maximum, such as `0...255`. The loop skips its body when `count <= a`, and Adder includes the maximum number of turns in the frame cost.
- **Longer jumps in `asm` blocks**: Conditional branches (`beq`, `bne`, `bcc`, `bcs`, `bmi`, `bpl`, `bvc`, `bvs`) can now reach beyond the 6510's `-128...127` byte range. Adder expands a branch that needs more reach into an inverted branch followed by a `jmp`.

### Changed

- **Less work when only part of the state changes**: Reactive bindings now share compact change flags, including flags for individual rows in small lists. Idle frames can skip unchanged groups with one check. Frame costs for `if / else` handlers and single-row list updates include only the outputs those paths can reach.
- **Cheaper keyboard checks and consistent timer reads**: Checking `if System.keyboard.stroke then` or `if System.keyboard.dropped then` now tests for an event without copying its 6-byte record. Reads of multi-byte variables changed by `System.clock.interrupt` now recheck the high byte, keeping timer updates from producing a mixed value.
- **Set one color for a text row**: Text regions can now use `System.screen.color[row][a..<b] <- color` with one `Color` value per row. These bindings also work alongside `asm` blocks that leave the region's screen addresses and variables alone.

## Lab & Guide v0.5.13 · Language v0.8.13 (2026-10-22)

### Changed

- **Clearer keyboard and joystick guidance**: The Guide explains how both joystick ports share keyboard wiring, why simultaneous controls can hide or invent key readings, and how to choose and test the combinations your program supports.

## Lab & Guide v0.5.15 · Language v0.8.15 (2026-10-22)

### Added

- **Four background colors for text**: Use `System.screen.extended_background` with `ScreenCode(glyph:, background:)` for the video chip's four-background text mode. Bind `System.screen.extended_background <- (first:, second:, third:)` alongside `System.screen.background`, and choose glyphs and backgrounds with `ScreenCode(glyph: 0...63, background: 0...3)`.
- **Fill the rest of a font (`Charset(glyphs, fill:, map:)`)**: Build a full 256-character `Charset` from a shorter list of `Glyph` values. Use `fill: blank_glyph` to fill the remaining slots automatically.
- **Sine waves for whole numbers (`phase.sine(lo...hi)`)**: Turn a `0...255` phase angle into a whole number in `lo...hi` or `lo..<hi`. Build a table at compile time with `(0..<256).map(i -> i.sine(0...63))`, or use a shared 256-byte lookup table at run time.

### Changed

- **Faster table reads and 2D loops**: When loops and `.map(...)` read 256-entry tables with steps such as `table[base +% i * step]` or `table[base -% i * step]`, Adder can advance the index instead of multiplying on every turn. It also unrolls short inner loops over 2D screen and color grids, matching the speed of hand-unrolled loops.

## Lab & Guide v0.5.14 · Language v0.8.14 (2026-10-22)

### Changed

- **Smaller, faster private byte updates**: Eligible increments and decrements use one processor instruction while preserving checked arithmetic and hardware writes. The private-field benchmark falls from 22 to 16 kernel cycles and uses eight fewer program bytes. The Guide reflects the smaller cost of guarded byte updates.

## Lab & Guide v0.5.13 · Language v0.8.13 (2026-10-22)

### Changed

- **Clearer keyboard and joystick guidance**: The Guide explains how both joystick ports share keyboard wiring, why simultaneous controls can hide or invent key readings, and how to choose and test the combinations your program supports.

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

- **Find your way around code in the Lab**: Jump to a symbol or `include` file with `F12` or `Cmd`/`Ctrl`-Click, find references with `Shift+F12`, rename symbols with `F2`, and open the symbol outline with `Cmd`/`Ctrl+Shift+O`. The Lab highlights reads and writes across files. Apply compiler-checked fixes from the error tooltip or with `Cmd`/`Ctrl+.`.

## Lab & Guide v0.5.10 · Language v0.8.11 (2026-10-21)

### Added

- **Editor support through a language server (`adder lsp --stdio`)**: Use Adder in any editor with Language Server Protocol support. The server provides multi-file diagnostics, fixes checked by the compiler, completions, hovers, signature help, definitions, references, renaming, document symbols, formatting, and inline byte and cycle costs. Browser and desktop tools can also use `@adder/compiler/lsp` and `@adder/compiler/service`.
- **Universal VS Code extension (`adder-vscode.vsix`)**: Write, inspect, and run Adder programs in desktop VS Code and in the browser on `vscode.dev` with syntax highlighting, inline cycle and byte cost hints, side-by-side cost and assembly reports, and an embedded Commodore 64 emulator panel with automatic virtual disk mounting and hot-reload on save.

### Changed

- **Shared language intelligence and binding hovers in the Lab**: Hovering over `const`, `var`, and `<-` bindings now shows their resolved type details alongside hardware, callable, and cost summaries.

## Lab & Guide v0.5.9 · Language v0.8.10 (2026-10-21)

### Changed

- **Smaller, faster bounded division in fast code**: Whole-number division can now use a small shared table when the declared range fits. The division-by-320 example drops from 537 to 470 program bytes and from a 2,232-cycle frame bound to 84, with checked arithmetic preserved. Ordinary and small code keep their compact choice.
- **Tighter costs for a copy that runs once**: A simple bounded loop that copies a list and clears its Boolean guard now counts that copy once. Every guard test still counts, generated programs are unchanged, and the Lab and Guide explain the bound.
- **Cheaper typed keyboard input**: Stroke and dropped-input readers now share the native line editor's bounded repeat helper. The sample's frame bound falls from 8,992 to 5,163 cycles, keeping the same typing behavior, queue capacity and input timing.
- **Safer memory limits for large lists**: The final memory check now includes lists filled at startup and alignment, keeping ordinary data out of I/O addresses. Adder still accepts a layout that fits after placement.
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

- **New `Plasma` example in `Learn Adder`**: Try a 60 fps dithered plasma in `3. Graphics & Assets`. It uses an 8-glyph Bayer dither charset, four background colors, per-cell color RAM, and a sprite overlay banner.

### Changed

- **Faster screen and color-RAM loops**: Loops that fill several rows of screen cells and colors can now run in one pass ahead of the raster beam when the frame's work finishes before it reaches the bottom row. Indexed table reads and fixed column offsets also use direct indexed instructions, avoiding extra temporary copies.
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

- **Smaller, faster helper functions**: Adder now keeps known integer bounds through nested function calls. When every caller supplies values that fit, the helper can skip repeated checks and use less working memory. Wider callers keep their safeguards.
- **Quicker row updates through helpers**: Loops can calculate a stable row address once even when user functions update its cells or windows. Nested calls and overlapping copies keep their usual order.
- **Less temporary struct storage**: Private struct fields can use their original values directly, and harmless overwritten field assignments disappear along with unused workspace.
- **Correct snapshots and failure locations in mutable helpers**: Local constants keep the value they captured before a parameter changes, and failed result checks report the helper's result line.
- **Correct values through shared methods**: Methods used with different bounds preserve every call's values, including projected text rows and event counters.

## Lab & Guide v0.5.6 · Language v0.8.4 (2026-10-20)

### Changed

- **Smaller programs using structs**: Repeated method calls on the same sized struct now share compiled code and working memory, reducing program size for text regions, collections, and user-defined structs while preserving their behavior.
- **Correct callback choices from changing helpers**: Struct methods that update a passed variable now return the selected callback correctly across repeated calls.
- **Less working memory and setup for functions**: Unused local values and harmless unused assignments now need no storage or instructions. This also removes word-wrapping workspace when printing only characters. Runtime checks and checked loop counters keep their safeguards.
- **Smaller, quicker page updates**: Full-screen text programs now use a complete scroll whenever it fits the frame, even when printing only every few frames. Hello World gets smaller and completes each scroll in one frame. Programs that present one row at a time also leave out an unused copy routine.
- **Smaller, faster repeated printing**: Fixed text passed through functions and methods can stay in the program's constant tables. Short lines that always start at the left edge skip unnecessary wrapping work, and loops that fill a stable row calculate its address once. Hello World uses less program and working memory.
- **Method arguments keep their original values**: A read-only method keeps the receiver it acquired before evaluating a later argument that changes the same object.

## Lab & Guide v0.5.6 · Language v0.8.3 (2026-10-20)

### Changed

- **Larger source files**: Adder no longer limits `.adder` source to 65,535 characters. Large projects and comments can grow independently of the Commodore 64 memory limit, which still applies to the compiled `.prg`.
- **Streamlined Language Reference**: Replaced BNF grammar notation boxes and the separate Grammar Summary chapter with direct examples and keyword/operator tables in the Language Reference.

## Lab & Guide v0.5.5 · Language v0.8.2 (2026-10-20)

### Added

- **Ready-to-share disks and cartridges**: Download projects as PRG, D64, D71, D81, or auto-booting Magic Desk and EasyFlash cartridges from the Lab or command line. Companion data travels with the program, and disk exports no longer need an extra host tool.
- **Working files in the Lab**: Programs can load, save, copy, and append file bytes on virtual drives 8–11. Bounded streams work on a C64 too, and cartridge programs can read their bundled assets directly from ROM banks. Snapshots retain mounted disks and open files; reloading the same Lab project keeps its saved files.

## Lab & Guide v0.5.4 · Language v0.8.1 (2026-10-20)

### Added

- **Standalone `adder` command-line tool**: Start a project with `adder new`, choosing Sprite & Sound, Text & Input, Bitmap Canvas, or Minimal. Compile with `adder compile`, inspect byte and cycle costs with `adder costs`, and format `.adder` source with `adder format`.

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

- **Build tables and fonts at compile time**: Pure functions can now run inside `const` declarations, including functions with local variables, `for` loops, `if`, and `match`, plus `.map` over constant ranges. Calls such as `isqrt(0..<256)` and `Charset(glyph_fn(0..<256))` put the finished data into your `.prg`, with zero runtime CPU cost.

### Changed

- **Desktop window controls**: Made window title bars and close boxes easier to grab and added full Port 2 joystick cursor and window dragging alongside 1351 mouse support.

## Lab & Guide v0.4.1 · Language v0.6.0 (2026-10-18)

### Added

- **Bounded strings (`String<N>`)**: Fixed-capacity ASCII strings with `{...}` interpolation, `++` concatenation, fast slices and trimming, character editing, number formatting and parsing, and live display through `Text` and `TextPage`.
- **Typed higher-order functions**: Functions can accept and return other functions (such as `fn(Digit): Digit`), and list `.map` and `.filter` work with both named functions and inline closures.
- **In-place `mut` parameters**: Pass variables, struct fields, and list items with `mut` so helper functions can update caller state in place without copying, while automatically refreshing any screen bindings that depend on them.
- **Background work progress**: Long-running background `work` jobs can report live status with `publish value`, giving your main loop a clean `.progress` snapshot each frame alongside `.running`.
- **More capable `when` cases and interrupts**: Mode `case` blocks can own screen bindings, placed views, queues, background jobs, and scroll settings. Adder cleans these up when you switch modes. Raster and timer interrupts now support local variables, control flow, helper calls, and inline `asm`, with full cycle budget checks.
- **New String & callback examples**: Added complete greeting, command parser, high-score, and calculator projects, plus an interactive digit-transform example in the Guide.
- **Help for the new language features**: The editor and Guide now cover `String<N>`, function values, `mut` parameters, `publish value` progress, and interrupts. Autocomplete, hovers, signature help, and line costs explain these features. Hovers and source costs also show which variables a call modifies.

### Changed

- **Faster `.map`, `.filter`, and string comparisons**: Inlined known callbacks inside `.map` and `.filter` (including hardware sprite loops) and sped up short string and slice comparisons.
- **Faster `match` dispatch and division**: Dense numeric `match` blocks now use jump tables, and constant division can use lookup tables. Frequently used loop variables get priority in zero-page memory. Full-screen tile maps also need less startup and idle work.
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
