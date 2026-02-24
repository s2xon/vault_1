# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## What This Repo Is

This is an Obsidian personal knowledge vault — not a software project. There is no build system, no tests, and no linter. All files are Markdown with YAML frontmatter.

---

## The Core Workflow

**Read `.claude-context.md` first every session.** It's the source of truth for vault state.

The workflow is:
1. User drops rough notes in the vault root (messy, typos, informal — that's intentional)
2. Claude sorts them: cleans phrasing, adds frontmatter, adds backlinks, moves to the right folder
3. Update `.claude-context.md` to reflect any structural changes made

The user writes their own notes — do not ghost-write lecture notes or journal entries. Clean them up, don't replace them.

---

## Vault Structure

```
Home.md                  — Dashboard/nav hub
.claude-context.md       — Session reference (read first)
Obsidian Workflow.md     — How the system works

School/
  School.md              — Course hub
  CS361/ CS362/ CS340/   — Empty course templates (active but not yet populated)
  CS381/
    CS381 - Notes.md
    Stack Machines.md
    Types and Polymorphism.md
    CS381 - Assignment 5.md

Projects/Conn/           — 5 interconnected design docs for the Conn meetup app
Ideas/                   — Idea dump + individual idea notes
Fitness/                 — PPL workout tracker
Daily Notes/             — One file per day, format: YYYY-MM-DD.md
Images/                  — All pasted images (Obsidian auto-saves here)
```

---

## Frontmatter Requirements

Every note must have:

```yaml
---
aliases:
  - Alternate Name
tags:
  - tag
  - tag/subtag
---
```

Aliases make Obsidian suggest the note when typing `[[`. Tags control graph view colors and filtering.

---

## Tag System

| Tag | For |
|-----|-----|
| `#school` | Anything school-related |
| `#school/cs361` | CS 361 — Software Engineering I |
| `#school/cs362` | CS 362 — Software Engineering II |
| `#school/cs340` | CS 340 — Intro to Databases |
| `#school/cs381` | CS 381 — Programming Language Fundamentals |
| `#cs/vm` | Virtual machines, bytecode, interpreters |
| `#cs/compilers` | Compilers, parsing, code generation |
| `#project` | Any project work |
| `#project/conn` | Conn app |
| `#fitness` | Workouts, lifting, health |
| `#idea` | Random ideas |
| `#nav` | Navigation/dashboard pages |
| `#daily` | Daily notes |

When a new topic doesn't fit existing tags, create a new one and add it here and in `.claude-context.md` and `Obsidian Workflow.md`.

---

## Internal Linking Conventions

- Use `[[Page Name]]` for wikilinks
- Use `[[Page Name|Display Text]]` when the display text should differ
- Hub pages (Overview, course hubs, Home) should link down to their sub-pages
- Sub-pages should link back up: `Part of [[CS381 - Notes]]`
- Related pages should cross-link naturally — don't force it

---

## Graph View Colors

| Query | Color |
|-------|-------|
| `tag:#school` | Blue |
| `tag:#fitness` | Green |
| `tag:#project` | Purple |
| `tag:#idea` | Yellow |
| `tag:#inbox` | Red |
| `tag:#nav` | Gray |

---

## Active Projects Summary

**Conn App** (`Projects/Conn/`) — In-person/online meetup app. Genre-based groups, accomplishments, stars/recognition, meetup types, user profiles. Five interconnected design docs.

**School** — Four active CS courses. CS381 has real notes; CS361/362/340 are templates not yet populated.

**Lifting Tracker** — PPL split. Table-based session log. Copy-paste template per session. PR table at the top.

---

## When Organizing Root-Level Notes

1. Check for existing folder/tag before creating new ones
2. If it's a business/project idea → `Ideas/`
3. If it's a personal system/habit note → `Ideas/`
4. If it's a course assignment → `School/CSXXX/`
5. If it's a daily log → `Daily Notes/` with filename `YYYY-MM-DD.md`
6. After moving, update `.claude-context.md`
