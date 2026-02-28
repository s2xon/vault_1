# Claude Memory — vault_1

## Vault Identity
Obsidian personal knowledge vault. No build system. All files are Markdown with YAML frontmatter.
Owner: Saxon. Working directory: /Users/saxon/Documents/vault_1

---

## Session Workflow
1. Read `.claude-context.md` first (source of truth for vault state)
2. Check vault root for unsorted `.md` files — sort them every session
3. Clean phrasing, add frontmatter, add backlinks, move to right folder
4. Update `.claude-context.md` after any structural changes
5. Do NOT ghost-write lecture notes or journal entries — clean them up, don't replace them

---

## Backlink Convention (ALWAYS enforce this)

Every note must have a clear chain up and down. The hierarchy is:

```
Home → School → [Course Hub] → [Topic Note] → [Leaf Note]
Home → School → CS Catch-Up Roadmap → Algorithms Catch-Up → Algorithms - Ch1 Recursion
                                                            → (future leaves: Ch2, Quicksort notes, etc.)
```

Rules:
- Hub pages link **down** to all their sub-pages
- Sub-pages link **back up** with `Part of [[Parent]]` or `Back to [[Parent]]`
- Every new leaf note must have `Part of [[DirectParent]]` at the top
- When creating a new chapter/topic note, ALSO update the parent hub to add a downward link
- When a topic gets its own note later (e.g. Quicksort), that note becomes the new leaf and the old section in Algorithms Catch-Up should link to it

Current chain integrity:
- Home ✅ → School ✅ → CS Catch-Up Roadmap ✅ → Algorithms Catch-Up ✅ → Algorithms - Ch1 Recursion ✅
- School ✅ → CS381 - Notes ✅ → Stack Machines ✅ / Types and Polymorphism ✅ / CS381 Assignment 5 ✅
- School ✅ → CS362 - Notes ✅ → CS362 - Project ✅
- School ✅ → CS361 - Notes ✅ (no leaves yet)
- School ✅ → CS340 - Notes ✅ (no leaves yet)

---

## Frontmatter Requirements
Every note must have:
```yaml
---
aliases:
  - Alternate Name
tags:
  - tag
---
```

---

## Tag System
| Tag | For |
|-----|-----|
| `#school` | Anything school-related |
| `#school/cs361` | CS 361 |
| `#school/cs362` | CS 362 |
| `#school/cs340` | CS 340 |
| `#school/cs381` | CS 381 |
| `#cs/vm` | Virtual machines, bytecode, interpreters |
| `#cs/compilers` | Compilers, parsing, code generation |
| `#cs/algorithms` | Algorithms catch-up notes |
| `#project` | Any project work |
| `#project/conn` | Conn app |
| `#fitness` | Workouts, lifting, health |
| `#idea` | Random ideas |
| `#daily` | Daily notes |
| `#finance` | Finance, MECOP, financial goals |
| `#review` | Daily productivity reviews |

---

## Deep Dive Companion Docs
Every chapter/topic note the user writes gets a companion `[Note Name] - Deep Dive.md` in the same folder.
- Link from source note: add `— deep dive: [[Note Name - Deep Dive]]` to the `Part of` line at the top
- Deep dive covers: fuller examples, things missed, exam-worthy facts, worked problems, comparisons
- Existing deep dives: `Algorithms - Ch1 Recursion - Deep Dive`, `Stack Machines - Deep Dive`, `Types and Polymorphism - Deep Dive`
- When a new chapter note is created → create its deep dive immediately

## Finance Folder
`Finance/` — hub is `Finance.md`. Contains `MECOP.md` (Oregon State co-op program tracker) and `Financial Goals.md`. Tag: `#finance`. Link Finance from Home.

## Claude Notes Sections
Every school content note should have a `## Claude Notes` section at the bottom (before Related) with corrections, clarifications, or things worth flagging. Add this when creating or cleaning up any school note.

---

## Daily Log
`Daily Notes/Daily Log.md` — index of all daily notes + reviews, newest first. Update this every session when a new daily note or review is created.

## Review Structure
```
Reviews/
  Reviews.md         ← hub, back to Home
  Daily/             ← one per day, format: YYYY-MM-DD Review.md
  Monthly/           ← one per month, format: YYYY-MM MonthName.md
  Yearly/            ← one per year, format: YYYY.md
```
- Wikilinks resolve by filename in Obsidian — moving files doesn't break links
- Every session: update the current month's review (Monthly/YYYY-MM MonthName.md) with new patterns, observations, and advice based on new daily reviews
- Monthly review links up to Yearly, Yearly links up to Reviews hub
- When writing a new daily review, also add a row to Reviews.md daily table and update the monthly review

---

## User Preferences
- Reviews go in `Reviews/` folder, not inline in daily notes
- Daily notes link to their review with `[[YYYY-MM-DD Review]]`
- Keep user's voice in personal notes — fix typos and structure, don't rewrite
- Main tasks + subtasks format preferred for daily todos
- User has ADHD — reviews should be honest, structured, and constructive (see 2026-02-24 Review.md for tone reference)
