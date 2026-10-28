---
title: What Claude Can Do in James
order: 9
---

# What Claude Can Do in James

Every session in James gives Claude a set of extra tools that plain Claude Code doesn't have. You don't need to set anything up. Just ask in plain words.

Tools that change things outside the conversation (starting processes, opening sessions, creating jobs) ask for your approval like any other tool, unless your permission mode allows them. Reading and writing your notes, todos and plans never asks.

## Plan and hand off

Claude keeps a goal list with steps and a progress log pinned above the message box, so you can see where a long task stands at a glance.

When the context fills up, Claude can write a **handoff** (what was done, decisions, key files and the next step) and continue in a fresh session without losing the thread.

> "Context is getting full. Write a handoff and continue in a new session."

## Ask you for things: Todos

When Claude needs a decision, a review or something only you can do, it puts a todo in your inbox instead of waiting in a session you might not be watching. It can attach files and notes, reply on the todo's thread, and report back when it finishes work you asked for.

Claude can never approve, dismiss or delete a todo, and can't close a **Decide** todo. Those are yours. See [Todos](./todos.md).

> "Put the React upgrade decision in my inbox with the options and your recommendation."

## Schedule work: Jobs

Claude can create, edit, pause and run scheduled jobs: a prompt that runs on its own as a new session, daily, weekly or once. It can also look through past runs and their results. See [Jobs & Runs](./jobs.md).

> "Every weekday at 9am, summarize yesterday's commits and save it to the Vault."

## Remember things: Vault

Claude can save, search, read and update notes in your [Vault](./vault.md), a knowledge base shared by every session and project. Notes are never deleted, only archived, and every change is versioned.

> "Research MCP auth patterns and save a summary to the Vault under references."

## Run long commands in the background

Builds, test suites and migrations run as background tasks owned by James. They keep going even if the session restarts, and Claude is told when they finish.

> "Run the full test suite in the background and tell me when it's done."

## Start and stop your app

Claude can save how your project runs (web, API, Storybook…), start it in its own terminal, and give you the local URL. Running launches show up in the project menu and the bottom bar, where you can restart or stop them.

> "Set up how this project runs, then start it and give me the URL."

## Use your terminals

Claude can read the output of terminals you have open, and, only when you ask, open a new terminal or type into one (including keys like Ctrl+C). Typing into a terminal **always** asks for approval, whatever your permission mode.

> "Open a terminal and start a Python REPL."

## Browse the web (desktop app)

In the desktop app, Claude gets its own hidden browser. It can open pages (including your local dev server), click, type, scroll, read the page and take screenshots, for example to check your UI at phone width. It only shows the window if you ask to see it, and asks before opening more than one.

> "Open localhost:5173, log in with the test account, and screenshot the dashboard at phone width."

## Show you plans and images

Claude can open an HTML or Markdown plan or mockup from your project in a tab next to the chat. The tab refreshes when the file changes, and you can pin comments on HTML plans. It can also show images inline in the chat.

> "Make an HTML wireframe for the settings page and show it to me."

## Organize projects and sessions

Claude can create workspaces, add a folder as a project, and open a new session in another project, optionally with a first message.

> "Create ~/code/new-app, add it to my Work workspace, and open a session there to scaffold a Vite app."

## Track features and bugs

In projects that use a `.workflow/` folder, Claude can list, create and update feature, bug and improvement specs: tick acceptance criteria, log progress and decisions, and move items between backlog, active and archive. See [Work Items](./workflow.md).

> "Create a feature spec for dark mode and tick criteria as you finish them."

## Trim what each project loads

Claude can show which skills, MCP servers and agents a project actually uses, and save a slimmer **preset** for it so each turn costs fewer tokens. Applying a preset always asks first.

> "Trim this project's preset down to the skills and MCP servers we actually use."
