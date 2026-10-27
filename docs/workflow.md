---
title: Work Items
order: 8
---

# Work Items

If your project keeps feature specs, bug reports and improvements as Markdown in a `.workflow/` folder, James shows them in a panel and lets Claude keep them up to date as it works.

## The folder

```
.workflow/
├── features/       backlog/  active/  pending-review/  archive/
├── bugs/           backlog/  active/  pending-review/  archive/
└── improvements/   backlog/  active/  pending-review/  archive/
```

Each item is a folder (for example `features/active/FEAT-012-dark-mode/`) with an `index.md` holding its description, a checklist of acceptance criteria, and a progress log. The folder it sits in is its status.

## The Features & Docs panel

Open it from the session ⋮ menu → **Features & Docs**, or click the active-item count next to a project in the sidebar.

- **Overview** — what needs attention, what's in progress, what's up next, and current plans.
- **Items** — everything, grouped by Active, Pending review, Backlog and Archive. Open one to see its spec, progress and files, or click **Continue** to pick it up in a session.
- **Docs** — plans, release notes, `docs/`, steering docs and Markdown files at the project root.

James flags items that need tidying — no criteria, stale for 14 days, duplicate ids, all criteria done but still active — and **Tidy up work items** sends Claude a request to fix them.

## Working with Claude

> "Create a feature spec for dark mode and put it in active."
>
> "Continue FEAT-012."

When a session works on an item, Claude ticks criteria as they're done and logs progress and decisions, so the next session (or you) can see exactly where things stand. If Claude changes code without updating the item, James reminds it.

Claude moves an item to the archive only after you confirm it's done.
