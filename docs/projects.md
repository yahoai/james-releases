---
title: Projects & Git
order: 3
---

# Projects & Git

A project is a folder on your Mac that Claude works in. Projects are grouped into workspaces in the sidebar.

## Adding a project

Press **⌘⇧O** (or **+** next to a workspace in the **Projects** sidebar). Browse to the folder, or paste a path (`~` works), and click **Add Project**.

To remove a project, use its ⋮ menu → **Remove from Workspace**. This never deletes any files.

## Workspaces

Workspaces group projects, for example "Work" and "Personal". Use **+** at the top of the Projects sidebar to add one, and the workspace's options menu to rename or delete it. Move a project with its ⋮ menu → **Move to workspace…**, or **Pin to top** to keep it in the **Pinned** box.

Each project row shows small badges: the number of uncommitted changes (amber), a dot when something is launched, and **missing** if the folder no longer exists.

## The project menu

Click the project name in the header to open its menu:

- **Launches** and **Terminals** for the project. See [Terminals & Launches](./terminals.md)
- **Features & Docs**: see [Work Items](./workflow.md)
- **Browse Files**, **Open in Finder**, **Copy Path**
- **View .claude Config**: the project's commands, agents, skills, hooks and settings (read-only)
- **Extensions Usage**: which skills, MCP servers and agents this project actually uses
- **Project Settings...**

## Project settings

- **Default permission mode**: new sessions in this project start in this mode on every device.
- **Default launch command**: for example `pnpm dev`. Saved to `.claude/james-launch.json` in the project, so you can commit it and share it.
- **Auto-start**: start the default command when a session opens (this Mac only).

## Files

**Browse Files** opens a file tree. Click a file to view it with syntax highlighting, or rendered if it's Markdown. The viewer is read-only, so ask Claude to make changes.

## Git

The branch badge in the header shows the current branch, the number of changed files, and how far you are ahead of or behind the remote. Click it to open the git panel:

- **Changes**: stage or unstage files, write a message (or click **AI Generate**), then **Commit** or **Commit & Push**.
- **History**: recent commits. Click one for details.
- **Pull** appears when you're behind the remote.

If a project contains several repositories, you pick one from a list first.
