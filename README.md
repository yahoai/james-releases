# James Desktop — Releases

James is a remote Claude Code client: run Claude Code sessions from anywhere, across multiple projects, with split views, terminals and dev server management.

This repository hosts the desktop app builds. Download the latest version from **[Releases](https://github.com/yahoai/james-releases/releases/latest)**.

## Requirements

- macOS 11 or later (Apple Silicon)
- [Node.js](https://nodejs.org) installed
- [Claude Code](https://docs.anthropic.com/claude-code) CLI installed and logged in

Builds are signed with a Developer ID and notarized by Apple.

## Claude Code plugins

This repository is also a Claude Code plugin marketplace (`plugins/`).

```bash
claude plugin marketplace add yahoai/james-releases
claude plugin install james-routines@james
```

| Plugin | What it does |
|---|---|
| `james-routines` | Manages a repo's `.workflow/routines/` folder — routine files that James runs on a schedule |
