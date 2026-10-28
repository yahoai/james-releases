---
title: Terminals & Launches
order: 4
---

# Terminals & Launches

## Terminals

Press **⌘T** to open a terminal in the current project. Terminals live in the bottom bar, which **⌘J** shows or hides. Each terminal belongs to a project and keeps running when you switch to another project.

Claude can read the output of your open terminals. It only types into one when you ask, and always asks for approval first.

## Launches

A launch is a long-running process for your project, such as a dev server, an API or Storybook.

Click **Launch…** (in the project menu or the **Launches** tab of the bottom bar) and pick:

- a **saved command** from `.claude/james-launch.json`
- a script from `package.json` (James suggests the right one, and uses your package manager)
- or **Use custom command** to type any shell command

When the process prints a local address (like `http://localhost:5173`), James shows a `:5173 ↗` badge you can click to open it. Until then the launch shows as starting.

Status dots: green = running, amber = starting, red = crashed, grey = stopped. Use **Restart** and **Stop** from the project menu or the launch card, and **Show logs** to see its output.

To start your app automatically whenever you open a session, set a **Default launch command** and turn on **Auto-start** in **Project Settings...**.

### `.claude/james-launch.json`

```json
{
  "defaultCommand": "pnpm dev",
  "commands": [
    { "name": "web", "command": "pnpm dev" },
    { "name": "api", "command": "cd api && uv run fastapi dev" }
  ]
}
```

Commit this file to share your launch commands with your team. Claude can write it for you: "Set up how this project runs."

## Background tasks

Long builds and test runs that Claude starts in the background are owned by James, so they keep running even if the session restarts. A spinner with a count appears in the status bar while any are running. Click it to see all of them, or stop one.
