# gh-copilot-vim

`gh-copilot-vim` is a GitHub CLI extension that wraps `gh copilot` in a vim-mode REPL.

## Why an extension (not a Copilot CLI plugin)?

Copilot CLI slash commands like `/vim` are currently hardcoded in the Copilot CLI binary. The plugin API does not expose a way to register custom slash commands. A `gh` extension is the closest supported path for this experience today.

## Install

```bash
gh extension install user3301/gh-copilot-vim
```

If `prompt_toolkit` is not available, the executable prompts to install it on first run.

## Usage

```bash
gh copilot-vim
gh copilot-vim --effort high --yolo
```

Supported forwarded flags:

- `--effort`
- `--model`
- `--yolo`
- `--allow-all`
- `--add-dir` (repeatable)

Every prompt is sent to:

```bash
gh copilot -p "<text>" --continue -s [forwarded flags]
```

## REPL controls

- Starts in vim mode
- `/vim` toggles vim mode on/off
- `:q` / `:quit` exits
- `Ctrl+D` / `Ctrl+C` exits

Bottom toolbar statusline:

- vim ON + insert: `[ VIM ] -- INSERT --  |  model: default  |  effort: default  |  turn: 0`
- vim ON + normal: `[ VIM ] -- NORMAL --  |  model: default  |  effort: default  |  turn: 0`
- vim OFF: `[ -- ]  |  model: default  |  effort: default  |  turn: 0`
- active flags are appended when enabled, for example: `⚡ yolo` and `✓ allow-all`
