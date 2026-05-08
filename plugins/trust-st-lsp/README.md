# trust-st-lsp

[![license](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue)](LICENSE)

IEC 61131-3 Structured Text language server for Claude Code. Wires the `trust-lsp` binary into Claude Code's built-in LSP plugin integration so the agent gets diagnostics, navigation, hover, symbols, and call hierarchy on `.st` files.

## Supported Extensions

`.st`

## What you get

| Capability | Surface |
|---|---|
| Diagnostics | automatic post-edit |
| Jump to definition | LSP tool |
| Find references | LSP tool |
| Hover (type info, IO declarations, doc comments) | LSP tool |
| Document & workspace symbols | LSP tool |
| Call hierarchy (incoming + outgoing) | LSP tool |
| Implementations | LSP tool |

## Installation

The plugin runs the `trust-lsp` binary that Claude Code launches per session — you supply the binary, the plugin tells Claude Code which extensions to map to it.

### 1. Install the `trust-lsp` binary

#### Linux / macOS — prebuilt

Pick the archive for your architecture from the [truST releases page](https://github.com/johannesPettersson80/trust-platform/releases/latest):

| Platform | Archive |
|---|---|
| Linux arm64 (Pi 5) | `trust-lsp-linux-arm64.tar.gz` |
| Linux x86_64 | `trust-lsp-linux-x64.tar.gz` |
| macOS arm64 | `trust-lsp-darwin-arm64.tar.gz` |
| macOS x86_64 | `trust-lsp-darwin-x64.tar.gz` |

Install into `~/.local/bin`. Pi 5 / Linux arm64:

```bash
mkdir -p ~/.local/bin
curl -L https://github.com/johannesPettersson80/trust-platform/releases/latest/download/trust-lsp-linux-arm64.tar.gz \
  | tar -xz -C ~/.local/bin
chmod +x ~/.local/bin/trust-lsp
```

Swap `linux-arm64` for `linux-x64`, `darwin-arm64`, or `darwin-x64` on other platforms.

Or, if you prefer a single line that survives a paste:

```bash
mkdir -p ~/.local/bin && curl -L https://github.com/johannesPettersson80/trust-platform/releases/latest/download/trust-lsp-linux-arm64.tar.gz | tar -xz -C ~/.local/bin && chmod +x ~/.local/bin/trust-lsp
```

#### Windows — prebuilt

Download `trust-lsp-win32-x64.zip` from the releases page, extract it, and add the directory containing `trust-lsp.exe` to your `PATH` (System Properties → Environment Variables → `Path`).

#### From source (any platform)

```bash
git clone https://github.com/johannesPettersson80/trust-platform
cd trust-platform
cargo install --path crates/trust-lsp
```

This drops `trust-lsp` in `~/.cargo/bin`, which is usually on `PATH` already.

### 2. Confirm it's on `PATH`

```bash
which trust-lsp
# expected: /home/<you>/.local/bin/trust-lsp   (or wherever you installed it)
```

If `which` returns nothing, your shell's `PATH` doesn't include the install directory. On Raspberry Pi OS and most Debian-based systems, `~/.local/bin` gets added by `~/.profile` on next login. To pick it up in the current shell:

```bash
export PATH="$HOME/.local/bin:$PATH"
```

> **Don't try to verify with `trust-lsp --help` or `trust-lsp --version`.** The binary has no CLI surface — it expects LSP JSON-RPC on stdin and will block silently waiting for a client. Use `which trust-lsp` to confirm presence; let Claude Code launch the server.

### 3. Install the plugin in Claude Code

In a Claude Code session opened at your truST workspace:

```text
/plugin marketplace add johannesPettersson80/trust-claude-plugins
/plugin install trust-st-lsp@trust-claude-plugins
```

Open any `.st` file. Run `/plugin` and check the **Errors** tab — empty means the server started. If you see `Executable not found in $PATH`, step 2 didn't take in the shell that launched Claude Code: re-export `PATH` (or restart your shell) and re-launch Claude Code.

## More

- [truST repository](https://github.com/johannesPettersson80/trust-platform)
- [LSP specification](https://github.com/johannesPettersson80/trust-platform/tree/main/site/public/reference/specifications/14-lsp)
- [Marketplace overview](https://github.com/johannesPettersson80/trust-claude-plugins)
