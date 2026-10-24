# Changelog

Updates to the Adder language, Lab and Guide.

## Lab & Guide v0.5.49 · Language v0.9.0 (2026-10-24)

### Added

- **Reusable Pool callbacks**: Pass an inline function or a saved callback to a Pool's `step`, `any` or `first`. Local snapshots let a callback use settings sampled for that call, while updates keep their existing order and checks.

### Fixed

- **Clearer Pool callback errors**: Invalid callback forms now receive source-level errors instead of failing inside the compiler.

## Lab & Guide v0.5.47 · Language v0.8.41 (2026-10-24)

### Changed

- **A shared Adder identity**: Lab uses compact typography, while Guides, Welcome and the splash have more room to read. A lowercase wordmark and slanted warm bars connect them.
- **Offline Guide fonts**: Generated Guides include their fonts, styles and licenses so they look the same when opened locally.

### Fixed

- **A calmer welcome**: Read the startup note in a roomier dialog with simple tabs, steady scrolling and a Continue button that stays in view.

### Added

- **Self-playing Snake**: The splash starts a Snake game that eats, grows and restarts on its own, with warm colors spread along its entire body.

## Lab & Guide v0.5.46 · Language v0.8.41 (2026-10-24)

### Added

- **Full release history**: Browse every release on the new Changelog page, linked from the Language Guide and Lab.

### Changed

- **Recent releases in the Lab**: The Lab's changelog now shows the five most recent releases.

## Lab & Guide v0.5.45 · Language v0.8.41 (2026-10-24)

### Changed

- **Clearer bounds and ranges**: Read bounds and ranges more easily in Lab and VS Code: type brackets follow the type color, and range markers follow numbers. Comparisons, arrows and pipes keep their usual quiet styling.

## Lab & Guide v0.5.44 · Language v0.8.40 (2026-10-24)

### Added

- **Writable windows**: Name a slice or rectangle over mutable or mapped memory and edit its cells directly with a writable window.
- **Share complete settings**: Share related settings with interrupts using `Publication`. Each read gets a complete old or new value, and saved copies stay unchanged.
- **Compile-time deadlines**: Set a deadline with `before(line:)`. Adder checks at compile time that a frame handler finishes, or a raster interrupt returns, before that line.

## Lab & Guide v0.5.43 · Language v0.8.39 (2026-10-24)

### Added

- **Publishing interrupt settings**: Use `Publication(initial:)` to share related settings with screen and timer interrupts. Saved copies stay unchanged when you publish updates.
- **Flexible publication updates**: Build a replacement with list functions or pipes, then publish it directly or from a foreground `action`. Failed updates keep the previous value.

### Fixed

- **REU handle checks**: Publications and work progress now reject REU handles, which cannot be copied as ordinary values.
- **Read-only published values**: REU transfers can no longer overwrite a publication's current value. Copy it into a `var` when you need to edit it.
- **Clearer error locations**: Read-only and interrupt errors now point to the calls you wrote and explain how to fix them.

## Lab & Guide v0.5.42 · Language v0.8.38 (2026-10-24)

### Added

- **Editable window cells**: Named windows over variables or mapped memory let you edit selected cells, including rectangles. Use a `var` for a separate copy.

### Fixed

- **Compact rectangle copies**: Rectangular copies keep compact row-copy code when their bounds are known.
- **Rectangle bounds checks**: An invalid rectangle now stops before writing any of its cells.
- **Mapped REU transfers**: The reference evaluator now handles REU fetches and swaps into mapped memory correctly.
- **Restored mapped outputs**: Mapped outputs now restore their values after a handler or REU transfer overwrites them, even when the output value hasn't changed.

## Lab & Guide v0.5.41 · Language v0.8.37 (2026-10-24)

### Added

- **Piped list calculations**: Write calculations left to right with `|>` or `:>`, using list functions such as `map`, `filter` and `reduce`.
- **Sensor desk example**: Try Sensor desk to learn list calculations and log a whole batch with `action` and `do`.
- **Compile-time assertions**: Check constant relationships with `#assert condition, "message"`. Failed checks point to your code; passing checks add no runtime work.
- **Longer calculations**: Let long calculations take several display refreshes with `#allow frame_skips`. Adder still checks timing-sensitive work and reports the gap between updates.

### Changed

- **Consistent list functions**: List calculations now use standalone functions and explicit callbacks. The examples, Guide and editor help use the same spelling.
- **Shared map work**: Consecutive numeric `map` calls can now share work and memory when their calculations cannot fail.

### Fixed

- **List and action fixes**: Piped and direct sprite calculations now agree on positions. Character lists also work with formatted digits, and actions work through included files.
- **Compact sprite positions**: Sprite positions using named numeric limits now compile as compactly as those using literal limits.

## Lab & Guide v0.5.40 · Language v0.8.36 (2026-10-24)

### Added

- **Pipes and lists in practice**: Sensor desk teaches list calculations, missing readings and whole-batch logging. The Quickstart also introduces pipes with a runnable example.

### Fixed

- **Correct sprite positions**: Fixed sprite positions in inline and piped calculations.
- **Character lists and included actions**: `append` now accepts character lists with `digits()` results. Actions in included files work as they do in a single file.

## Lab & Guide v0.5.39 · Language v0.8.35 (2026-10-24)

### Added

- **Actions in pipelines**: Use `action` for screen and region work inside a pipeline. `do(value, action)` runs the action once for the whole value, then passes that value onward.

## Lab & Guide v0.5.38 · Language v0.8.34 (2026-10-24)

### Added

- **Fixed-list transformations**: Transform fixed lists with `map`, `filter`, `reduce` and `scan`. Other helpers combine lists, search them, or rearrange their entries.
- **List functions as callbacks**: Give a standard list function a complete type signature to reuse it as a callback. Your own functions can still use the same names.

### Changed

- **Shared map calculations**: Compatible consecutive numeric maps now share intermediate work and memory.
- **Consistent list semantics**: List calculations use standalone functions and explicit callbacks. Filtering keeps slot positions, and `count` counts present values, including `false`.

## Lab & Guide v0.5.37 · Language v0.8.33 (2026-10-24)

### Added

- **Function pipes**: Pass a value into the next function with `|>` or the Commodore-friendly `:>`. Both spellings work with named functions and function values.

## Lab & Guide v0.5.36 · Language v0.8.32 (2026-10-24)

### Changed

- **Leaner REU stores**: REU stores from stable mapped memory can avoid temporary copies when the source is guaranteed to stay unchanged.
- **Smaller, faster text programs**: Some text programs now use less memory and run faster.

### Fixed

- **Consistent REU fills**: REU fills now work through the command line and project API as well as standalone source.

## Lab & Guide v0.5.35 · Language v0.8.31 (2026-10-23)

### Fixed

- **Steady iPhone address entry**: The Ultimate address input stays in place when the iPhone keyboard opens, making addresses easier to enter.
- **Welcome waits for you**: The welcome screen no longer interrupts if you start using the Lab while it loads; open it yourself when you are ready.

## Lab & Guide v0.5.34 · Language v0.8.31 (2026-10-23)

### Fixed

- **Steady phone address entry**: Ultimate address entry keeps focus as phone keyboards open or resize, and search fields in the top-bar menus stay usable.

## Lab & Guide v0.5.33 · Language v0.8.31 (2026-10-23)

### Changed

- **Responsive Lab editing**: Keep editing while compilation, C64 startup, language help, image work and project saves run in the background without freezing the editor or controls.
- **Smoother large projects**: Large projects open more smoothly as the Lab loads optional panels on demand, reuses unchanged files and displays long listings a screenful at a time.

### Fixed

- **Sound when you choose**: Typing and Run no longer open an audio device; enable sound from the C64 controls, or retry unavailable sound while the program keeps running silently.
- **Finish image edits first**: Run, Save, downloads and project switching wait for accepted image edits. The Lab warns before leaving unsaved work and explains how to retry interrupted background tasks.
- **Virtual disk files retained**: Changing REU settings keeps files already saved to the mounted virtual disk.

## Lab & Guide v0.5.32 · Language v0.8.31 (2026-10-23)

### Added

- **REU hardware choices**: Choose a 128 KiB to 16 MiB REU in Lab or VS Code, with optional images and Commodore or Ultimate behavior. Lab checks image sizes and keeps mounted disks when restarting; a stock C64 remains the default.

## Lab & Guide v0.5.31 · Language v0.8.31 (2026-10-23)

### Added

- **REU storage in Adder**: Detect an REU and its capacity, then store, fetch, swap, verify or fill byte windows across banks. Frame costs include DMA time; the Guide covers insufficient expansion memory.

## Lab & Guide v0.5.30 · Language v0.8.30 (2026-10-23)

### Added

- **REU hardware emulation**: Hosts can emulate 128 KiB to 16 MiB REUs with preloaded images and Commodore, Ultimate or Ultimate extended behavior. Transfers share machine time with the display and timers; snapshots retain expansion data and controls.

### Fixed

- **Sprite and REU timing**: NTSC sprite transfers use the correct bus slots across scanline boundaries, and REU transfers preserve CPU bus access when a display pause ends.

## Lab & Guide v0.5.30 · Language v0.8.29 (2026-10-23)

### Added

- **Shared Adder libraries**: Share stateless functions between Adder projects in `.addl` libraries (WIP), with automatic call checks, memory layout and initialization. Initial support takes one or two byte inputs and returns a byte.
- **Library inspection and help**: Inspect library functions and requirements in the CLI or Lab; completions, signatures and hovers use the same interface and refresh when it changes.
- **Compiled library example**: Try Compiled Math Lab to call a shared library and see its results. The Guide covers building, inspecting and using libraries with the installed CLI, plus assembly callers.

## Lab & Guide v0.5.29 · Language v0.8.28 (2026-10-23)

### Added

- **Exported C64 functions**: Export stateless functions for C64 programs (WIP), with one or two byte inputs, a byte result, chosen addresses, safety checks and resource costs. The Guide includes an assembly caller.

### Changed

- **Faster repeat builds**: Switching projects and undoing edits builds faster by reusing recent results. Edited code still gets checked, and compiler integrations can keep their own caches.
- **Lighter list loops**: Some short loops that mark or move list entries need less setup; Adder uses the shortcut when the complete program gets smaller and faster within its limits.
- **Smaller repeated messages**: Repeated message endings can share more code. Snake saves another 16 bytes with the same startup, message and frame costs.

### Fixed

- **Installed CLI examples**: Follow library and assembly examples using installed `adder` commands and local files, with instructions for copying generated bindings and loading both programs.

## Lab & Guide v0.5.26 · Language v0.8.23 (2026-10-22)

### Changed

- **Shared message endings**: Repeated message endings take less space. Snake saves 72 bytes without extra memory or slower startup or frames; source costs still count all executed work.

## Lab & Guide v0.5.26 · Language v0.8.22 (2026-10-22)

### Changed

- **Less loop setup**: Some short loops that mark or shift list entries need less setup, without using more memory or slowing startup.

## Lab & Guide v0.5.26 · Language v0.8.21 (2026-10-22)

### Changed

- **Smaller wrapping updates**: Some bounded wrapping counter updates compile to smaller, faster code while preserving the same values and checks.

## Lab & Guide v0.5.26 · Language v0.8.20 (2026-10-22)

### Changed

- **C64 keyboard and joystick**: Open or hide on-screen C64 keyboard and Joystick 2 controls, with latched directions, sticky modifiers and key banks. They open by default on touch screens; a shorter layout leaves more screen space.

## Lab & Guide v0.5.25 · Language v0.8.20 (2026-10-22)

### Changed

- **Fewer repeated color fills**: Setting a constant screen color with constant row, column or region accents avoids redundant per-frame fills; Adder draws those accents at startup.

## Lab & Guide v0.5.25 · Language v0.8.19 (2026-10-22)

### Changed

- **Lighter C64 emulation**: The C64 emulator uses less temporary memory and copies less state at breakpoints. Cycle counts follow bus activity, with corrected handling of disabled interrupts during display pauses.

## Lab & Guide v0.5.24 · Language v0.8.19 (2026-10-22)

### Fixed

- **Accessible CLI help**: The command-line Guide replaces an inaccessible repository link while keeping public cost documentation and built-in command help available.

## Lab & Guide v0.5.23 · Language v0.8.19 (2026-10-22)

### Changed

- **Faster VS Code help**: VS Code completions and hints respond faster and stay available during background builds. Editing refreshes the help for your code.
- **Single assembly view**: The cost pane shows authored assembly once, with source links, branch navigation and cost figures still available.
- **CLI quick reference**: The Guide adds a quick CLI reference for projects, compilation, costs, formatting and the language server, linked from Quickstart and supported by fuller command help.

## Lab & Guide v0.5.22 · Language v0.8.19 (2026-10-22)

### Changed

- **Project checks in VS Code**: VS Code checks included files in their project context, finds shared declarations, labels and assets, and keeps inline costs attached to the right source when switching files or reusing builds.
- **Costs beside your code**: Click compact cost hints beside your code. The pane shows source costs, indented assembly and scrollable project totals; an optional editor frame summary starts off.
- **Language help without builds**: Get completions, signatures, hovers and navigation without building or loading assets, even with incomplete calls. Hovering no longer measures costs, and unused-`fast` checks avoid compilation.

- **Loop and byte examples**: The Guide explains loops with changing ends, and the authoring skill covers byte access. Examples use blank-font padding in the splash and shorter room and character-map code in Undercrypt.

## Lab & Guide v0.5.21 · Language v0.8.16 (2026-10-22)

### Changed

- **Snake and Classics**: Conduit is now Snake in Classics, alongside Jupiter Lander, Mystify and Plasma after the learning path; all four remain on the examples disk.

## Lab & Guide v0.5.20 · Language v0.8.16 (2026-10-22)

### Changed

- **Source and assembly together**: Explore bytes, cycles and assembly for each source file, follow branches and copy selections. Cost views follow unsaved edits, and the Lab frame meter links to busy code.

- **Compact toolbar in narrow windows**: Narrow windows move Hot load and downloads into More, keeping primary commands on one row. Phones group Guide and device actions there; wide windows keep dedicated controls.

## Lab & Guide v0.5.19 · Language v0.8.16 (2026-10-22)

### Changed

- **Editor options nearby**: Formatting, wrapping, text size and phone cost visibility sit beside the editor, with Options on phones; desktop About and release notes sit beside Guide and Ko-fi.
- **Compact build status**: Running status and build figures share one compact line; scroll the figures on narrow screens with touch or keyboard to reach every value.

## Lab & Guide v0.5.18 · Language v0.8.16 (2026-10-22)

### Changed

- **Clearer Lab command layout**: Desktop Guide, Ko-fi and More sit beside the title, with Run, Save and device actions below; sending to Ultimate and its settings share one control.

### Fixed

- **Single button outlines**: Disabled toolbar buttons keep one clean outline while retaining their larger touch targets.

## Lab & Guide v0.5.17 · Language v0.8.16 (2026-10-22)

### Changed

- **Grouped commands and status**: Project, run, download and help actions stay grouped, while status and build figures move below the workspace; phones use a compact Stats control.
- **Easier menu navigation**: Menus stay within the window, support keyboard navigation and restore focus when closed; larger touch targets and one More destination simplify About and release history.

## Lab & Guide v0.5.16 · Language v0.8.19 (2026-10-22)

### Changed

- **Storage for record lists**: Adder chooses different record-list layouts when they save memory or CPU cycles without increasing other program costs.

## Lab & Guide v0.5.16 · Language v0.8.18 (2026-10-22)

### Changed

- **Shared output calculations**: Related outputs can share an integer calculation, making some programs smaller or faster without extra storage or slower startup.

## Lab & Guide v0.5.16 · Language v0.8.17 (2026-10-22)

### Changed

- **Shared output change checks**: Related consecutive outputs can share change checks without changing timing or order. Signal Test saves 16 program bytes and 20 worst-case frame cycles.

## Lab & Guide v0.5.16 · Language v0.8.16 (2026-10-22)

### Added

- **Read and write bytes**: Use `.lo` and `.hi` to read bytes from two-byte whole-number expressions as `Number<u8>`, or assign them on a `Number<u16>` variable without masks or division.
- **Loops with changing bounds**: Use changing upper bounds in loops such as `0..<count` when their integer types have known maxima; empty ranges skip, and frame costs include the maximum turns.
- **Longer assembly branches**: Conditional branches in `asm` can reach beyond `-128...127` bytes; Adder adds a longer jump when needed, so more assembly labels stay reachable.

### Changed

- **Less work for unchanged state**: Reactive bindings share compact change flags, including rows in small lists; idle frames skip unchanged groups, and frame costs follow the outputs each path can reach.
- **Keyboard checks and timer reads**: Keyboard `stroke` and `dropped` conditions avoid copying six-byte records; multi-byte variables changed by timer interrupts recheck the high byte to avoid mixed values.
- **Colors for text rows**: Color a text-row slice with one `Color` value using `System.screen.color[row][a..<b] <- color`, alongside assembly that leaves its screen addresses and variables alone.

## Lab & Guide v0.5.13 · Language v0.8.13 (2026-10-22)

### Changed

- **Keyboard and joystick guidance**: The Guide explains how joysticks share keyboard wiring, which combinations can cause misleading key readings, and how to test supported controls.

## Lab & Guide v0.5.15 · Language v0.8.15 (2026-10-22)

### Added

- **Four text backgrounds**: Use four text backgrounds with `System.screen.extended_background` alongside `System.screen.background`, then pick each character's glyph and background with `ScreenCode(glyph: 0...63, background: 0...3)`.
- **Fill unused font slots**: Fill a 256-character font from a shorter glyph list with `Charset(glyphs, fill:, map:)`, using `fill: blank_glyph` for unused slots.
- **Whole number sine waves**: Turn a `0...255` phase into a whole-number sine wave with `phase.sine(lo...hi)`, using tables built at compile time or a shared 256-byte runtime table.

### Changed

- **Faster table and grid loops**: Stepped reads from 256-entry tables can run faster in loops and `.map(...)`. Short inner loops over 2D screen and color grids can match hand-written speed.

## Lab & Guide v0.5.14 · Language v0.8.14 (2026-10-22)

### Changed

- **Smaller private byte updates**: Eligible private byte increments and decrements use one instruction. The private-field example drops from 22 to 16 cycles and saves eight bytes; the Guide reflects these costs.

## Lab & Guide v0.5.13 · Language v0.8.13 (2026-10-22)

### Changed

- **Keyboard and joystick guidance**: The Guide explains how joysticks share keyboard wiring, which combinations can cause misleading key readings, and how to test supported controls.

## Lab & Guide v0.5.12 · Language v0.8.13 (2026-10-22)

### Fixed

- **Reliable graphics startup**: Large projects initialize sprites, fonts and screens correctly and restore their original contents when you run the program again.

## Lab & Guide v0.5.12 · Language v0.8.12 (2026-10-22)

### Changed

- **Smaller fixed-point calculations**: Bounded coordinate and fixed-point calculations use less memory and code. Mandelbrot shrinks from 2,898 to 2,043 bytes, with worst-case frame costs falling from 15,163 to 2,695 cycles.
- **Quicker list results and loops**: List-building functions copy less data, and eligible private byte loops run faster. The 40-cell example's worst-case frame cost falls from 2,393 to 2,076 cycles.
- **Cheaper frame updates**: Values written every frame cost less to update, while change events, histories and device writes keep their existing behavior.
- **Updated frame cost examples**: The Guide's oversized-frame messages now reflect the smaller generated programs.

## Lab & Guide v0.5.11 · Language v0.8.11 (2026-10-21)

### Added

- **Code navigation in the Lab**: Use `F12` for definitions and `include` files; the Lab also adds references, renaming, a symbol outline, cross-file read/write highlights and compiler-checked fixes.

## Lab & Guide v0.5.10 · Language v0.8.11 (2026-10-21)

### Added

- **Editor language server**: Use `adder lsp --stdio` for editor diagnostics and fixes, navigation, renaming, completion, formatting and byte/cycle costs. Integrations can use `@adder/compiler/lsp` and `@adder/compiler/service`.
- **VS Code extension**: Use `adder-vscode.vsix` in desktop VS Code or `vscode.dev` for highlighting, byte/cycle hints, cost/assembly reports and a C64 emulator with automatic disk mounting and reload-on-save.

### Changed

- **Binding details on hover**: Lab hovers for `const`, `var` and `<-` bindings show resolved types alongside hardware, function and cost details.

## Lab & Guide v0.5.9 · Language v0.8.10 (2026-10-21)

### Changed

- **Faster bounded division**: Bounded division in `fast` code can use a shared table; ordinary and `small` code keep their compact approach. The divide-by-320 example shrinks from 537 to 470 bytes and from 2,232 to 84 worst-case frame cycles.
- **Tighter guarded copy costs**: Costs for a bounded list-copy loop count a copy once when its Boolean guard is cleared, while still counting every guard test. The Lab and Guide explain the bound.
- **Cheaper typed input**: Typed keyboard input uses less frame time, with the same typing and queue behavior. The sample's worst-case frame cost falls from 8,992 to 5,163 cycles.
- **Accurate list memory checks**: Memory checks account for startup-filled lists and alignment, keeping ordinary data outside I/O addresses and accepting final layouts that fit.
- **Clearer video standard errors**: The emulator rejects unsupported video standards with a clear error, leaving the running machine and pending audio unchanged.

## Lab & Guide v0.5.8 · Language v0.8.9 (2026-10-21)

### Changed

- **Visible screens with timers**: Text and bitmap displays start normally in hardware-timer programs, including those whose raster routines begin inactive.
- **Reliable timer program compilation**: Timer programs compile correctly when they need private temporary storage, and working-memory reports match the bytes actually reserved.
- **Quicker native keyboard input**: The native keyboard editor leaves more frame time for other work alongside assembly and interrupts on PAL and NTSC, with unchanged typing behavior.

## Lab & Guide v0.5.8 · Language v0.8.8 (2026-10-21)

### Changed

- **Cost details at a glance**: Hover or focus a cycle figure for cost and memory details, then open it in the 6502 inspector's Woven or Flow view.
- **See what calls change**: Call costs and hovers describe changes with the names you wrote, with exact fields, ranges and helper details available when needed.
- **Clearer inspector costs**: The inspector distinguishes each line's bytes from shared and deferred work, with labels for unknown, declared, trusted and per-loop-turn costs.

## Lab & Guide v0.5.7 · Language v0.8.7 (2026-10-21)

### Changed

- **Smaller arithmetic for packed coordinates**: Multiplying or dividing by 256 and other large powers of two produces smaller code for packed coordinates, with the same range checks.
- **Cheaper hardware cell bindings**: Bindings reading fixed hardware-array cells use less code, memory and update time. Whole-array reads, slices and changing indexes keep their existing checks.
- **Accurate text frame errors**: Oversized text scenes report the frame limit and required cycles without false overlap errors. Adder also stops retrying text options that are already disabled.
- **Expansion reads and project loading**: The emulator reads back expansion-port writes when no cartridge owns `$DE00` through `$DFFF`. Projects load faster by skipping dependency and build folders.

## Lab & Guide v0.5.7 · Language v0.8.6 (2026-10-21)

### Added

- **Plasma example**: Try the 60 fps `Plasma` example in `Learn Adder`: dithered graphics, four background colors, per-cell colors and a sprite banner.

### Changed

- **Faster screen and color loops**: Multi-row screen and color fills can run in one pass if the frame's work finishes before the beam reaches the bottom row. Indexed reads and column offsets also run faster.
- **Less repeated work**: Some loops and helpers produce smaller, faster code by reusing values across branches and calls.
- **Quicker private calculations**: Small private calculations use less memory and update faster, with the same event timing, sound changes and retained text.
- **Fewer record and list copies**: Functions returning records or lists can fill new local values directly, reducing copying and working memory.
- **Smaller numeric helpers**: Numeric helpers can produce smaller code for known byte values and constants, sharing code when a separate version would cost more.
- **Automatic savings in the Guide**: The Guide explains automatic size and speed savings that need no `fast` mark.
- **Cheaper repeated frame events**: Repeated frame events with the same interval can use less code and memory while keeping their schedules.
- **Cheaper list fills**: Loops that write fixed numbers into lists need less temporary storage and address setup, with existing index and value checks preserved.

## Lab & Guide v0.5.7 · Language v0.8.5 (2026-10-21)

### Changed

- **Release notes on return visits**: Returning to the Lab after an unseen release opens the Welcome dialog's `Changelog` tab, and dismissing it marks the entry as read.

## Lab & Guide v0.5.6 · Language v0.8.5 (2026-10-20)

### Changed

- **Faster bounded helper calls**: Helpers can run faster with less memory when all callers supply values within known bounds, even through nested calls.
- **Quicker row updates**: Row-update loops can run faster when helpers change cells or windows, while nested calls and overlapping copies keep their existing order.
- **Less temporary struct memory**: Private struct fields can use less temporary memory, and harmless overwritten assignments no longer need code or workspace.
- **Correct snapshots and failure locations**: Local constants in mutable helpers keep values captured before a parameter changes, and failed result checks point to the helper's result line.
- **Correct values in shared methods**: Methods shared across different value bounds preserve each call's values correctly, including text rows and event counters.

## Lab & Guide v0.5.6 · Language v0.8.4 (2026-10-20)

### Changed

- **Smaller struct programs**: Repeated methods on same-size structs can share code and memory, shrinking programs that use text regions, collections or your own structs.
- **Correct returned callbacks**: Struct methods that change a passed variable return the chosen callback correctly across repeated calls.
- **Less function setup and storage**: Unused locals and harmless unused assignments need no code or storage, and character-only printing no longer reserves word-wrapping space.
- **Smaller, quicker text scrolling**: Full-screen text can scroll in one frame whenever it fits, even with infrequent printing. Hello World and row-at-a-time text programs get smaller.
- **Smaller repeated printing**: Fixed-text printing, short left-aligned lines and stable-row fills need less repeated work. Hello World uses less program and working memory.
- **Correct method receiver snapshots**: Read-only methods keep the original receiver value when a later argument changes that same object.

## Lab & Guide v0.5.6 · Language v0.8.3 (2026-10-20)

### Changed

- **Larger source files**: Large `.adder` files and comments are no longer capped at 65,535 characters; compiled `.prg` files still have to fit the C64's memory.
- **Simpler Language Reference**: The Language Reference uses examples and keyword/operator tables instead of BNF boxes and a separate Grammar Summary chapter.

## Lab & Guide v0.5.5 · Language v0.8.2 (2026-10-20)

### Added

- **Disk and cartridge exports**: Export PRG, D64, D71, D81, Magic Desk or EasyFlash projects from the Lab or command line, including companion data and auto-booting cartridges. No extra disk tool is needed.
- **File operations and saved state**: Use virtual drives 8 through 11 for file operations, bounded streams on C64 hardware, and bundled ROM assets in cartridges. Snapshots keep disks and open files; project reloads keep saved files.

## Lab & Guide v0.5.4 · Language v0.8.1 (2026-10-20)

### Added

- **Standalone Adder command**: Create projects with `adder new`, including Sprite & Sound, Text & Input, Bitmap Canvas and Minimal templates. Compile, inspect costs and format source from the command line.

## Lab & Guide v0.5.3 · Language v0.8.1 (2026-10-20)

### Changed

- **Smaller canvas downloads**: Canvas `.prg` downloads omit empty working memory. `mystify.prg` shrinks by over 11 KB (90%) with unchanged frame speed.
- **Packed graphics assets**: Tile maps, fonts and sprites pack automatically and unpack before the first frame, saving over 6.6 KB in games such as `Scroller` and `Walker`.
- **Faster five-digit formatting**: Formatting 16-bit scores and counters with `.digits(5)` saves 350 to 850 cycles per call, leaving more frame time for HUD updates.
- **Smaller, faster disk files**: Sparse `Disk.save` and `Disk.load` data cuts 1541 save sizes and transfer times by 40% to 85%, with file-integrity checks on load.

## Lab & Guide v0.5.2 · Language v0.8.0 (2026-10-20)

### Added

- **Delete saved browser projects**: Delete old browser projects with the button beside each entry under `Project` > `Saved in this browser`.

## Lab & Guide v0.5.1 · Language v0.8.0 (2026-10-19)

### Added

- **Automatic source formatting**: Format `.adder` files with two-space indentation, consistent spacing and aligned data rows while preserving comments and inline assembly.
- **Editor wrapping and formatting**: Use `Wrap` for long editor lines without disturbing cycle costs, `Format` (`Shift+Alt+F`) for consistent source, and automatic indentation on `Enter`.
- **Simpler screen text bindings**: Bind strings, character arrays or single characters directly to `System.screen.text`, and use `.digits(N)` in choices, concatenation and interpolated strings.
- **Project entry files**: Set a folder project's entry file with `"entry"` in `project.json`, or let Adder use `main.adder`.
- **Guided learning chapters**: The project picker's `Learn Adder` examples are grouped into four chapters, with the file tree hidden for single-file examples and opened for multi-file projects.

### Changed

- **Clearer starter examples**: Early `Learn Adder` examples put the main idea at the top with less setup.

## Lab & Guide v0.4.2 · Language v0.7.0 (2026-10-19)

### Added

- **Constant tables and fonts**: Build tables and fonts in `const` declarations using pure functions, local variables, loops, branches and constant-range `.map`, with no runtime calculation.

### Changed

- **Easier Desktop window controls**: Desktop title bars and close buttons are easier to grab, and Port 2 joysticks can move the cursor and drag windows alongside the 1351 mouse.

## Lab & Guide v0.4.1 · Language v0.6.0 (2026-10-18)

### Added

- **Bounded ASCII strings**: Use fixed-capacity ASCII `String<N>` values with interpolation, concatenation, slicing, trimming, editing, number formatting and parsing, plus live display through `Text` and `TextPage`.
- **Functions as values**: Functions can accept and return typed functions such as `fn(Digit): Digit`, and list `.map` and `.filter` accept named functions or inline closures.
- **In-place mutable parameters**: Use `mut` parameters to let helpers update variables, struct fields and list items without copying, with dependent screen bindings refreshed automatically.
- **Background job progress**: Background `work` jobs can report progress with `publish value`, giving each frame a `.progress` snapshot alongside `.running`.
- **Mode resources and interrupt helpers**: Mode `case` blocks can own displays, queues, jobs and scrolling, with automatic cleanup on mode changes. Raster and timer interrupts gain locals, branching, helpers and `asm`, with cycle-budget checks.
- **String and callback examples**: Try complete greeting, command-parser, high-score and calculator projects, plus an interactive digit-transform example in the Guide.
- **Help for new language features**: The editor and Guide explain strings, function values, mutable parameters, background progress and interrupts, including costs and which variables calls change.

### Changed

- **Faster callbacks and comparisons**: Known callbacks in `.map` and `.filter` run faster, including hardware sprite loops, and short string and slice comparisons are quicker.
- **Faster matches and division**: Dense numeric `match` blocks and eligible constant division can run faster, and frequently used loop variables get priority in faster memory. Full-screen tile maps need less startup and idle work.
- **Updated learning examples**: `Flares` uses `flares.map(flare_sprite)`, Desktop reorders windows with `raise(mut wins, p)`, and the nav computer counts primes in a background job with a live progress bar.
- **Sound guidance and Atlas controls**: The Language Reference explains `Envelope` and `Tone` in more detail, and Atlas Studio has simpler tile-size and zoom controls.

### Fixed

- **Consistent background progress snapshots**: Multi-byte `.progress` and `String<N>` snapshots stay consistent across frames, including reads from raster or timer interrupts. They reset correctly when you reenter a mode.
- **Trailing spaces in keyboard input**: Submitted keyboard lines keep trailing spaces and their exact lengths.
- **Steadier mouse and paddle tracking**: The emulator tracks the 1351 mouse and paddles more steadily, without startup jumps.

## Lab & Guide v0.2.0 · Language v0.3.0 (2026-10-17)

### Added

- **Sound and sprite controls**: Control pulse and combined SID waveforms with full `Tone` settings, filters and volume. Read Voice 3's oscillator/envelope and use sprite expansion, priority, multicolor and collision flags.
- **Built-in game collections**: Use fixed-capacity `Pool` values for active game objects, `Ring` queues, shuffled `Deck` values, `Rect` hitboxes, frame `Cooldown` timers, `Wave` tables and `Flags` bitsets.
- **Disk jobs and file streams**: `System.drive[8...11]` supports reactive `load` and `save` jobs, bounded `file(name).read(capacity:)` streams and clear disk errors. Projects can export multiple `.d64` disks.
- **Canvas lines, paths and circles**: Draw lines, connected paths and exact midpoint circles on hires or multicolor canvases, with automatic background restoration and `.inverted` overlays.
- **Release notes in the Lab**: The Lab toolbar has a `Changelog` button, and the Welcome dialog has a `Changelog` tab.

### Changed

- **Consistent color names**: Use `color` for foregrounds, cursors and palettes, and `background` for canvas backgrounds in hires and multicolor modes.
- **Expanded learning examples**: Updated `Engine Room`, `Jupiter Lander`, `Deck Patrol` and `Crew Console` demonstrate SID filtering, `Rect.overlaps` hitboxes, `Pool` + `Cooldown` particle sparks and windowed drawing.
- **Clearer project entry badges**: Multi-file projects show an `entry` badge on the main file's editor tab and file-tree row, replacing the dot indicator.

## Lab & Guide v0.1.3 · Language v0.1.0 (2026-10-17)

### Changed

- **Compact Desktop example**: The Desktop (`Crew Console`) example combines its artwork into one sprite/tile sheet, compiling to 2,211 bytes with a worst-case frame cost of 5,204 cycles.

### Fixed

- **Ready-to-use artwork declarations**: Asset Studio tile entries copy `Picture(...)` declarations ready to use, and new layers inherit the entry's chosen color.

## Lab & Guide v0.1.2 · Language v0.1.0 (2026-10-17)

### Added

- **Artwork drawing tools**: Draw, fill, move, wrap, flip or clear artwork in Atlas & Charset Studio, with undo/redo, clickable neighboring previews and saved zoom/tool settings.

## Lab & Guide v0.1.1 · Language v0.1.0 (2026-10-17)

### Added

- **Browser Lab and Guide**: The browser Lab and Guide launch at `https://lab.adder.run/`, with an `Open the Lab` link from `https://adder.run/`.

### Changed

- **Refreshed example artwork**: Built-in examples have refreshed sprites, character sets and project descriptions.

## Lab & Guide v0.1.0 · Language v0.1.0 (2026-10-16)

### Added

- **Visible version numbers**: Check Language and Lab & Guide versions with `adder --version`, in the Lab toolbar and Welcome dialog, or in the Quickstart and Reference guides.
- **Welcome dialog**: The Welcome dialog shows emulator loading status, steps to start a project and release notes.
