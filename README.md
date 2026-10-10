# AILang Support for Visual Studio Code

Full-featured language support for AILang — the self-hosting, explicit-syntax systems programming language.

**Publisher:** 2Paws · **Version:** 1.2.2 · **Requires:** VS Code 1.75+

---

## Overview

This extension adds language support for `.ailang` files in VS Code, including:

- Syntax highlighting
- Compile and run commands
- Real-time diagnostics
- IntelliSense and symbol completion
- Manual/documentation browser
- Interactive flow graph for code relationships

The extension is designed to work with the AILang compiler and LSP tooling shipped with the project or placed in the workspace.

---

## Getting Started

1. Install the extension from the VS Code Marketplace or load it from a `.vsix` file.
2. Open any `.ailang` file. The extension activates automatically.
3. Ensure the AILang toolchain is available in your workspace or configured in settings.
4. Use the command palette or editor actions to compile, analyze, or run your file.

### Requirements

- **VS Code:** 1.75.0 or newer
- **Platform:** Native support is intended for Linux x86-64.
- **Windows:** Works through WSL.
- **macOS:** Not currently supported.

The extension expects the AILang tools to be present in the workspace or at a configured path.

### Tool setup

The extension looks for the compiler/LSP binaries in the project directory by default:

- `ailang.x` — compiler
- `ailang_lsp.x` — language server

If the binaries are elsewhere, set the path in VS Code settings.

---

## Features

### Syntax Highlighting

Full TextMate grammar for `.ailang` files, including keywords, pool types, builtins, control flow, strings, numbers, and comments.

### Compile and Run

Use the command palette or editor actions to compile and execute AILang programs.

Available commands:

- `AILang: Compile`
- `AILang: Run`
- `AILang: Analyze`
- `AILang: Open Documentation`
- `AILang: Show Flow Graph`

A run button also appears in the editor title bar for `.ailang` files.

### Real-Time Diagnostics

The LSP runs analysis passes automatically when you open or save a file.

Diagnostics cover issues such as:

- memory lifecycle problems
- control-flow errors
- data-flow problems
- unreachable code and recursion issues

### IntelliSense and Completions

The extension provides:

- AILang keywords and builtins
- file symbols
- scope-aware completion details
- shorthand expansion support

### Shorthand Aliases

Type abbreviated forms and the extension expands them to canonical AILang on accept.

Examples:

- `GT` → `GreaterThan`
- `LT` → `LessThan`
- `EQ` → `EqualTo`
- `FN` → `Function`
- `SR` → `SubRoutine`
- `IC` → `IfCondition`

A large built-in shorthand map is supported, and invalid shorthand that slips through is normalized on save.

### Documentation Sidebar

Click the AILang icon in the Activity Bar to browse local manuals in the extension's `docs/` folder.

Recommended reading order:

1. `Programming Intro to Ailang.md`
2. `AILANG Quick Syntax Reference.md`
3. `Basic Flow Control Guide.md`
4. `Memory Management Reference Manual.md`
5. `BNF grammar.md`

### Flow Graph

Open the interactive connectome with `AILang: Show Flow Graph`.

The graph shows how symbols relate within the codebase, including imports, pools, functions, subroutines, and loops. Nodes can be filtered, searched, and linked to source code.

---

## Commands

All commands are available via the Command Palette (`Ctrl+Shift+P`):

- `AILang: Compile`
- `AILang: Run`
- `AILang: Analyze`
- `AILang: Show Flow Graph`
- `AILang: Open Documentation`

---

## Configuration

Open VS Code Settings and search for `AILang` to configure the extension.

Available settings include:

- `ailang.lspPath` — path to the AILang LSP executable (`ailang_lsp.x`)
- `ailang.editor.shorthandDisplay` — show shorthand keyword names in the editor
- `ailang.editor.shorthandCustomMap` — custom shorthand overrides

Relative paths are resolved from the workspace root or the active document directory when appropriate.

---

## Troubleshooting

### No symbols or diagnostics appear

Check that `ailang_lsp.x` exists and is executable. If necessary, set `ailang.lspPath` to the correct location.

### Compile or run command does nothing

Make sure `ailang.x` is present and accessible. On Windows, the extension expects WSL to be available and paths to be valid from the Linux side.

### Completions do not include file symbols

Save the file once to trigger symbol refresh, or run `AILang: Analyze`.

---

## About AILang

AILang is a self-hosting systems programming language designed around radical explicitness. Every operation is a named function call, with no hidden behavior, implicit precedence, or runtime magic.

The compiler and tools are designed to be compact, self-contained, and native to Linux x86-64.

For more information, see the language project: https://github.com/AiLang-Author/Ailang-Self-Hosting-

---

## License

This extension uses a dual-license structure:

- **VS Code extension** (`extension.js`, package metadata, grammar, snippets, docs): [MIT License](LICENSE)
- **AILang compiler and tools** (`ailang.x`, `ailang_lsp.x`, and language source): [Sean Collins Software License (SCSL)](LICENSE-COMPILER.md)

Copyright (c) 2025–2026 Sean Collins, 2 Paws Machine and Engineering. All rights reserved.
