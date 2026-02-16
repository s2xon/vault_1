---
aliases:
  - Workflow
  - How To
tags:
  - nav
---
# Obsidian Workflow

This takes 10% of your time. The other 90% is actual work.

---

## The System

```
You write -> Inbox (or directly in a page) -> Claude organizes
```

That's it. Three rules:

1. **Capture fast** - Drop anything in [[Inbox]]. Don't think about folders or tags.
2. **Write your own notes** - Don't have AI write notes for you. It won't stick in your brain if you didn't write it.
3. **Let Claude clean up** - Point Claude to `.claude-context.md` and tell it to organize. It handles filing, tags, backlinks, and the graph view.

---

## Day-to-Day

| Situation | What to do |
|-----------|-----------|
| In class | Open the course page, write under current week |
| Random idea | Drop it in [[Inbox]] |
| Logging a workout | Copy template in [[Lifting Tracker]] |
| Project thoughts | Write in the project page or [[Inbox]] |
| End of week | Ask Claude to clean up inbox and add links |

---

## Tags

Tags let a note belong to multiple categories. Use these:

| Tag | For |
|-----|-----|
| `#school` | Anything school-related |
| `#school/cs361` | CS 361 specific |
| `#school/cs362` | CS 362 specific |
| `#school/cs340` | CS 340 specific |
| `#school/cs381` | CS 381 specific |
| `#project` | Project ideas and work |
| `#project/conn` | Conn app specifically |
| `#fitness` | Workouts, lifting, health |
| `#idea` | Random ideas, things to explore |
| `#inbox` | Unsorted, needs organizing |

You don't have to remember these. Just write. Claude will tag things for you.

---

## Backlinks

When you're writing and mention something that has its own page, type `[[` and link to it. Obsidian will suggest pages as you type.

Don't force links. If a connection is natural, make it. If not, don't. Over time, notes that matter will accumulate links on their own.

---

## Graph View Groups

Open graph view (`Cmd+G`) > click gear icon > Groups. Add these:

| Query | Color |
|-------|-------|
| `tag:#school` | Blue |
| `tag:#fitness` | Green |
| `tag:#project` | Purple |
| `tag:#idea` | Yellow |
| `tag:#inbox` | Red |
| `tag:#nav` | Gray |

---

## Plugins to Install

Go to Settings > Community Plugins > Browse. Install these:

1. **Obsidian Web Clipper** - Save articles/videos from your browser into the vault with one click
2. **Kanban** - Visual board for tracking assignments and tasks (optional)

That's it. Don't go down a plugin rabbit hole.

---

## What Claude Does

When you ask Claude to organize:
- Moves inbox notes to the right folder
- Adds frontmatter (tags, aliases)
- Adds backlinks between related notes
- Cleans up formatting
- Updates `.claude-context.md`
- Keeps the graph view colorful and connected
