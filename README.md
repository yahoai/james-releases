<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="James">
</p>

<h1 align="center">James</h1>

<p align="center">
  <strong>Your personal butler for Claude Code.</strong><br>
  Every project, every session, one window — on your Mac, in your browser, or on your phone.
</p>

<p align="center">
  <a href="https://github.com/yahoai/james-releases/releases/latest"><strong>Download for macOS</strong></a>
</p>

---

## Why James

Claude Code is powerful, but it lives in one terminal at a time. James gives it a home: open as many sessions as you like, see exactly what Claude is doing, and pick up right where you left off — from any device.

## What you get

**Work on everything at once**
Run sessions across all your projects side by side. Split the screen, compare, and switch with a click.

**Stay in control**
Approve tools before they run, review every change as a clear diff, and undo an edit when it isn't what you wanted.

**Your whole workbench in one place**
Terminals, your dev server, and git live right next to the conversation. Start your app with one click and open it straight from James.

**Take it with you**
Check in on a long task from your phone or another computer. Your sessions keep running while you're away.

**Know where your usage goes**
See your 5-hour and weekly limits at a glance, plus which sessions are using them.

**Let it work while you sleep**
Schedule routines that run on their own and report back when they're done.

**Make it yours**
Add plugins, MCP servers, skills and agents from Settings — no config files to edit.

## Get started

1. [Download the latest release](https://github.com/yahoai/james-releases/releases/latest) and drag James into Applications.
2. Make sure [Claude Code](https://docs.anthropic.com/claude-code) is installed and you're logged in.
3. Open James, add a project, and start your first session.

James updates itself automatically.

**Requirements:** macOS 11 or later on Apple Silicon, [Node.js](https://nodejs.org), and the [Claude Code](https://docs.anthropic.com/claude-code) CLI.
Builds are signed and notarized by Apple.

## Plugins

This repository is also a Claude Code plugin marketplace.

```bash
claude plugin marketplace add yahoai/james-releases
claude plugin install james-routines@james
```

| Plugin | What it does |
|---|---|
| `james-routines` | Set up routines that James runs for you on a schedule |
