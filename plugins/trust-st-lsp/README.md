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

The plugin requires the `trust-lsp` binary on your `$PATH`.

### Prebuilt binary

Download the archive for your platform from the truST [releases page](https://github.com/johannesPettersson80/trust-platform/releases/latest):

| Platform | Archive |
|---|---|
| Linux arm64 (Pi 5) | `trust-lsp-linux-arm64.tar.gz` |
| Linux x86_64 | `trust-lsp-linux-x64.tar.gz` |
| macOS arm64 | `trust-lsp-darwin-arm64.tar.gz` |
| macOS x86_64 | `trust-lsp-darwin-x64.tar.gz` |
| Windows x86_64 | `trust-lsp-win32-x64.zip` |

One-liner for Pi 5 / Linux arm64:

```bash
mkdir -p ~/.local/bin && curl -L https://github.com/johannesPettersson80/trust-platform/releases/latest/download/trust-lsp-linux-arm64.tar.gz | tar -xz -C ~/.local/bin && chmod +x ~/.local/bin/trust-lsp
```

Swap `linux-arm64` for the matching target on other platforms.

### From source

```bash
git clone https://github.com/johannesPettersson80/trust-platform
cd trust-platform
cargo install --path crates/trust-lsp
```

## Verify

```bash
trust-lsp --help
```

If Claude Code reports `Executable not found in $PATH` in the `/plugin` Errors tab, run `which trust-lsp` (Unix) or `where trust-lsp` (Windows) to confirm the binary location is on your shell's `PATH`.

## More

- [truST repository](https://github.com/johannesPettersson80/trust-platform)
- [LSP specification](https://github.com/johannesPettersson80/trust-platform/tree/main/site/public/reference/specifications/14-lsp)
- [Marketplace overview](https://github.com/johannesPettersson80/trust-claude-plugins)
