# trust-st-lsp

IEC 61131-3 Structured Text language server for Claude Code, providing diagnostics, hover, jump-to-definition, find references, document/workspace symbols, and call hierarchy on `.st` files.

## Supported Extensions

`.st`

## Installation

The plugin requires the `trust-lsp` binary on your `$PATH`.

### Linux / macOS (prebuilt)

Download the prebuilt binary from the [latest release](https://github.com/johannesPettersson80/trust-platform/releases/latest) and put it on your `$PATH`. For example, on Raspberry Pi 5 (arm64):

```bash
mkdir -p ~/.local/bin
curl -L https://github.com/johannesPettersson80/trust-platform/releases/latest/download/trust-lsp-linux-arm64.tar.gz \
  | tar -xz -C ~/.local/bin
chmod +x ~/.local/bin/trust-lsp
```

Replace `linux-arm64` with one of: `linux-x64`, `darwin-arm64`, `darwin-x64`.

### Windows

Download `trust-lsp-win32-x64.zip` from the [latest release](https://github.com/johannesPettersson80/trust-platform/releases/latest), extract it, and add the directory containing `trust-lsp.exe` to your `PATH`.

### From source

```bash
git clone https://github.com/johannesPettersson80/trust-platform
cd trust-platform
cargo install --path crates/trust-lsp
```

## Verifying the install

After installing, run:

```bash
trust-lsp --help
```

If Claude Code reports `Executable not found in $PATH` in the `/plugin` Errors tab, the binary isn't on your `PATH` — confirm with `which trust-lsp` (Unix) or `where trust-lsp` (Windows).

## More Information

- [truST repository](https://github.com/johannesPettersson80/trust-platform)
- [LSP specification](https://github.com/johannesPettersson80/trust-platform/tree/main/site/public/reference/specifications/14-lsp)
