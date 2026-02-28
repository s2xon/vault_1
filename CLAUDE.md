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

Keep tags flat and simple — one tag per topic/folder. No subtags. Tags create the central nodes in the graph view; navigation between notes is handled by backlinks, not tag hierarchy.

| Tag | For |
|-----|-----|
| `#cs` | Everything CS — courses, assignments, algorithms, deep dives, catch-up |
| `#project` | Any project — Conn app, side projects, anything being built |
| `#finance` | Finance, MECOP, budgets, financial goals |
| `#fitness` | Workouts, lifting, health |
| `#idea` | Random ideas, brainstorms |
| `#daily` | Daily notes |
| `#review` | Reviews — daily, monthly, yearly |

When a new topic doesn't fit existing tags, add a new flat tag and update this file, `.claude-context.md`, and `memory/MEMORY.md`.

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
| `tag:#cs` | Teal |
| `tag:#idea` | Yellow |
| `tag:#finance` | Orange |
| `tag:#inbox` | Red |

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
6. If it's finance/MECOP/goals content → merge into the relevant `Finance/` file
7. After moving, update `.claude-context.md`

---

## Automatic Behaviors (Do These Every Session Without Being Asked)

### Every Session
- Read `.claude-context.md` first
- Scan root for unsorted files and sort them
- Check for and clean up inline instructions left in notes (e.g. "claude please do X")

### When a New Daily Note Exists or Is Created
- Create the daily note in `Daily Notes/YYYY-MM-DD.md` with proper frontmatter
- Write a review in `Reviews/Daily/YYYY-MM-DD Review.md`
- Link the review from the daily note
- Add a row to `Daily Notes/Daily Log.md`
- Add a row to `Reviews/Reviews.md`
- Update `Reviews/Monthly/YYYY-MM MonthName.md` with new observations
- Update `Reviews/Yearly/YYYY.md` metrics if meaningful

### When a New Chapter/Topic Note Is Created
- Create a companion `[Note Name] - Deep Dive.md` in the same folder
- Add `— deep dive: [[Note Name - Deep Dive]]` to the `Part of` line in the source note
- Link the deep dive back to the source note and parent hub

### When Financial Info Is Provided (Pay Rate, Expenses, Goals)
- Calculate take-home pay after Oregon state + federal tax + FICA
- Build or update the monthly budget in `Finance/Financial Goals.md`
- Update `Finance/MECOP.md` with confirmed figures
- Update `Finance/Finance.md` current status table

### When New Notes Are Created
- Always add frontmatter (aliases + tags)
- Always add a `Part of [[Parent]]` backlink at the top
- Always update the parent hub to link down to the new note
- Add `## Claude Notes` section to school content notes
