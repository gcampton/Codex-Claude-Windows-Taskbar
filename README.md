![Windows](https://img.shields.io/badge/platform-Windows-blue)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Codex-Claude-Windows-Taskbar

A lightweight Windows taskbar widget for people using Codex and Claude Code.

This is a fork of [CodeZeno/Claude-Code-Usage-Monitor](https://github.com/CodeZeno/Claude-Code-Usage-Monitor). It keeps the original native Windows taskbar widget and adds Codex usage beside the Claude usage bars.

## What You Get

- A **5h** row showing Codex and Claude usage side by side
- A **7d** row showing Codex and Claude usage side by side
- Codex displayed as 5 blue squares
- Claude displayed as 5 orange squares
- A live reset countdown in the tray tooltip
- A small native widget that lives directly in the Windows taskbar
- A system tray icon with refresh, update frequency, language, startup, and exit options

## Requirements

- Windows 10 or Windows 11
- Claude Code installed and authenticated
- Codex installed and authenticated

Claude credentials are read from:

```text
~/.claude/.credentials.json
```

Codex credentials are read from:

```text
~/.codex/auth.json
```

Windows and WSL credential locations are supported.

## Build

Install Rust, then build from the repository root:

```powershell
cargo build --release
```

The executable will be written to:

```text
target\release\codex-claude-windows-taskbar.exe
```

## Use

Download the latest executable from the [Releases](https://github.com/gcampton/Codex-Claude-Windows-Taskbar/releases) page, then run it from PowerShell:

```powershell
.\codex-claude-windows-taskbar.exe
```

If built from source, run:

```powershell
.\target\release\codex-claude-windows-taskbar.exe
```

Once running, it appears in your taskbar and notification area.

- Drag the left divider to move the taskbar widget
- Right-click the widget or tray icon for refresh, update frequency, startup, language, and exit
- Left-click the tray icon to toggle the taskbar widget

## Diagnostics

Run:

```powershell
.\codex-claude-windows-taskbar.exe --diagnose
```

Logs are written to:

```text
%TEMP%\codex-claude-windows-taskbar.log
```

Settings are saved to:

```text
%APPDATA%\CodexClaudeWindowsTaskbar\settings.json
```

## Privacy And Security

This app reads local Claude and Codex OAuth credentials so it can call the same usage endpoints used by those tools.

What the app reads:

- Claude credentials from `~/.claude/.credentials.json`
- Codex credentials from `~/.codex/auth.json`
- The same files inside WSL distros when needed

What the app sends over the network:

- Requests to Anthropic endpoints for Claude usage
- Requests to ChatGPT/OpenAI endpoints for Codex usage
- Requests to GitHub only if update checking is used

What it does not do:

- It does not send your credentials to a separate backend
- It does not collect analytics or telemetry
- It does not upload your project files

## License

MIT. Original project copyright belongs to Code Zeno Pty Ltd.
