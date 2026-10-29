# Adder Releases

**Standalone CLI binaries, VS Code extension, and release notes for the [Adder](https://adder.run) Commodore 64 programming language.**

[**Website**](https://adder.run) · [**Adder Lab**](https://lab.adder.run) · [**Quickstart**](https://adder.run/quickstart.html) · [**Language Reference**](https://adder.run/reference.html) · [**Latest Release (v0.22.4)**](https://github.com/dylan/adder-releases/releases/latest)

---

## Install

Download the standalone `adder` executable or universal VS Code extension—no external runtime required:

| Platform | Architecture | Download | Checksum |
| :--- | :--- | :--- | :--- |
| **macOS** | Apple Silicon (`arm64`) | [`adder-darwin-arm64.tar.gz`](https://github.com/dylan/adder-releases/releases/latest/download/adder-darwin-arm64.tar.gz) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-darwin-arm64.tar.gz.sha256) |
| **macOS** | Intel (`x86_64`) | [`adder-darwin-x64.tar.gz`](https://github.com/dylan/adder-releases/releases/latest/download/adder-darwin-x64.tar.gz) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-darwin-x64.tar.gz.sha256) |
| **Linux** | `x86_64` (glibc) | [`adder-linux-x64.tar.gz`](https://github.com/dylan/adder-releases/releases/latest/download/adder-linux-x64.tar.gz) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-linux-x64.tar.gz.sha256) |
| **Linux** | `ARM64` (`aarch64`) | [`adder-linux-arm64.tar.gz`](https://github.com/dylan/adder-releases/releases/latest/download/adder-linux-arm64.tar.gz) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-linux-arm64.tar.gz.sha256) |
| **Windows** | `x86_64` | [`adder-windows-x64.zip`](https://github.com/dylan/adder-releases/releases/latest/download/adder-windows-x64.zip) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-windows-x64.zip.sha256) |
| **VS Code** | Universal (`.vsix`, Desktop & Web) | [`adder-vscode.vsix`](https://github.com/dylan/adder-releases/releases/latest/download/adder-vscode.vsix) | [`sha256`](https://github.com/dylan/adder-releases/releases/latest/download/adder-vscode.vsix.sha256) |

Extract the archive and place `adder` on your `PATH`:

```sh
# macOS (Apple Silicon)
curl -fsSL https://github.com/dylan/adder-releases/releases/latest/download/adder-darwin-arm64.tar.gz | tar -xz
sudo mv adder /usr/local/bin/adder
adder --version
```

## VS Code Extension

Download [`adder-vscode.vsix`](https://github.com/dylan/adder-releases/releases/latest/download/adder-vscode.vsix) for syntax highlighting, multi-file diagnostics, byte/cycle cost inlay hints, and an embedded C64 emulator Webview:

```sh
curl -fsSLO https://github.com/dylan/adder-releases/releases/latest/download/adder-vscode.vsix
code --install-extension adder-vscode.vsix
```

Or run **Extensions: Install from VSIX...** from the VS Code Command Palette.

---

## Quick Start

```sh
# Scaffold a new project interactively (project.json, src/main.adder, assets/)
adder new my-game

# Compile a project directory or single .adder file into a C64 .prg and .lbl symbol map
adder compile my-game -o out/my-game.prg

# Inspect static byte count, worst-case PAL/NTSC frame cycles, and 6510 assembly
adder costs my-game --listing

# Format .adder source files in place
adder format my-game

# Start the Language Server Protocol server over stdio
adder lsp --stdio
```

## License

Adder is released under the [MIT License](LICENSE).
