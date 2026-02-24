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
You write in root → Claude sorts, cleans up, adds links, creates folders/tags → moves to the right place
```

That's it. Three rules:

1. **Capture fast** - Drop new notes in the vault root. Don't think about folders or tags.
2. **Write your own notes** - Don't have AI write notes for you. It won't stick in your brain if you didn't write it.
3. **Let Claude clean up** - Point Claude to `.claude-context.md` and tell it to organize. It handles filing, tags, backlinks, and the graph view.

---

## Day-to-Day

| Situation | What to do |
|-----------|-----------|
| In class | Open the course page, write under current week |
| Random idea | Drop a new note in root or go straight to [[Ideas]] |
| Logging a workout | Copy template in [[Lifting Tracker]] |
| Project thoughts | Write in the project page or drop a note in root |
| Pasting an image | Obsidian saves it to `Images/` automatically — just paste |
| End of week | Ask Claude to sort root notes and add links |

---

## Tags

Tags let a note belong to multiple categories. You don't have to remember these — just write. Claude will tag things for you.

| Tag             | For                                        |
| --------------- | ------------------------------------------ |
| `#school`       | Anything school-related                    |
| `#school/cs361` | CS 361 — Software Engineering I            |
| `#school/cs362` | CS 362 — Software Engineering II           |
| `#school/cs340` | CS 340 — Intro to Databases                |
| `#school/cs381` | CS 381 — Programming Language Fundamentals |
| `#cs/vm`        | Virtual machines, bytecode, interpreters   |
| `#cs/compilers` | Compilers, parsing, code generation        |
| `#project`      | Any project work                           |
| `#project/conn` | Conn app specifically                      |
| `#fitness`      | Workouts, lifting, health                  |
| `#idea`         | Random ideas, things to explore            |
| `#nav`          | Navigation/dashboard pages                 |
| `#daily`        | Daily notes                                |
| `#cs/algorithms`| Algorithms study and catch-up              |
| `#review`       | Daily productivity reviews                 |

New tags get added here as the vault grows.

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

When you drop notes in root and ask Claude to organize:
1. Sorts root-level notes and figures out where they belong
2. Cleans up phrasing and fixes formatting
3. Adds frontmatter (tags, aliases)
4. Adds backlinks between related notes
5. Creates a new folder or tag if nothing fits yet
6. Moves the note to the right place
7. Updates `.claude-context.md` and the tag table above
