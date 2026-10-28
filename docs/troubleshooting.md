---
title: Troubleshooting
order: 13
---

# Troubleshooting

## "Claude Code is required"

James runs your sessions with the Claude Code CLI, which you install separately. The dialog shows the install command — copy it into Terminal:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Then run `claude` once in Terminal and log in. Back in James, click **Check again**.

If James says **Claude Code update recommended**, click **Update**.

## James won't start

The menu bar (tray) icon has **Restart Server** — try that first. If another program is using port 31010, quit it and restart James.

If James says it's already running, look for its icon in the menu bar, or quit it from there and open it again.

## "Disconnected. Reconnecting..."

James reconnects on its own. If it doesn't, click **Reconnect**, or use **Restart Server** from the menu bar icon.

On another device, check that Tailscale is connected and James is running on the Mac. See [Remote & Mobile](./mobile.md#troubleshooting).

## "Session is open on another device"

Only one device controls a session at a time. Click **Take control here** to continue on this one.

## A launch says "starting" forever

James marks a launch as running once it prints a local URL (like `http://localhost:3000`). If your command never prints one, it stays "starting" — it is still running. Use **Show logs** to check.

## Updates

James checks for updates shortly after it opens and every 6 hours, and asks before installing. To check now, use **Check for Updates…** in the menu bar icon.

## Where James keeps your data

| Folder | What's in it |
|---|---|
| `~/.claude-code-editor/` | sessions, settings, presets, todos and jobs |
| `~/James/vault/` | your [Vault](./vault.md) |
| `~/James/` | new projects and scratch sessions |
| `~/.claude/` | Claude Code's own history and settings (shared with the CLI) |

## Still stuck?

Open an issue at [yahoai/james-releases](https://github.com/yahoai/james-releases/issues) with what you did, what you expected, and what happened.
