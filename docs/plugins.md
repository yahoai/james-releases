---
title: Plugins & Extensions
order: 10
---

# Plugins & Extensions

Everything that extends Claude (plugins, MCP servers, skills, commands, agents and hooks) is in **Settings → Extensions**. No config files to edit.

## Plugins

The **Plugins** tab has three parts:

- **James plugins**: plugins made for James, from [yahoai/james-releases](https://github.com/yahoai/james-releases). **Install**, **Update**, turn on or off, or **Remove**. Use **Check for updates** to see new versions.
- **Other installed plugins**: install any Claude Code plugin by ID, in the form `name@marketplace` (for example `slack@claude-plugins-official`).
- **Marketplaces**: add a marketplace by `owner/repo` or git URL, and **Pull latest** to refresh it.

Plugins installed here are the same ones the `claude` CLI uses.

### james-routines

Keeps scheduled routines as files in your repo (`.workflow/routines/`) and registers them as James [jobs](./jobs.md). Ask Claude to "set up a routine" once it's installed.

## MCP servers

The **MCP** tab lists your MCP servers and whether they're active. Click **Add** and enter a name, a command (for example `npx`, `uvx` or `node`) and its arguments.

Choose the scope at the top: **Global (~/.claude)** for every project, or a specific project (saved in that project's `.claude` folder).

## Skills, commands, agents and hooks

These tabs list what's installed globally and in each project, from `.claude/skills/`, `.claude/commands/`, `.claude/agents/` and `settings.json`.

## Presets

Every MCP server, skill and agent a session loads costs tokens on every turn. A **preset** chooses which ones a project's sessions load.

- **Full** (the default) loads everything.
- Once a week James looks at what a project actually used and suggests a **Tailored** preset. Review it, then **Apply as project default**.
- Switch presets from the **Preset** button under the message box. Changes apply from the next turn.
- See all presets in **Settings → Presets**, or ask Claude: "Trim this project's preset down to what we actually use."
