# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A markdown-only Bible study scaffold. **There is no build system, no tests, no lint, no package manifest.** Every "file" is a `README.md` in a folder. Don't look for `npm`/`pip`/`make` commands — they don't exist. Tasks here are content edits, folder reorganization, and documentation.

## Layout on disk vs. layout in the docs — read this first

The published docs (`README.md`, `STRUCTURE.md`, `CONTRIBUTING.md`, `CHANGELOG.md`, `README-TEMPLATE.md`) consistently describe a layout rooted at `books-of-bible/` and `topics-of-study/`. **The filesystem does not match.** A refactor (commit `55df16f` and `02835da`) reorganized the repo to:

```
scripture/        # the 66 books (docs call this "books-of-bible/")
topics/           # cross-cutting themes (docs call this "topics-of-study/")
commentary/       # stub
people/           # stub
places/           # stub
resources/        # stub
theology/         # stub
words/            # stub (Hebrew/Greek word studies)
.personal/        # private notes (see two-layer model below)
.ai-chats/        # AI session logs (see protocol below)
```

The stub content folders each contain a one-line `# Read Me` placeholder. The 12-folder vision behind this layout is in `____bible-study-top-level-folders.md` (and its byte-identical duplicate `repo-planning.md`) — note that disk uses shorter names (`words/` not `word-studies/`, `topics/` not `topics-of-study/`) and is missing several folders from that vision (`_home/`, `timeline/`, `context/`, `teaching/`, `templates/`).

**Before "fixing" the inconsistency in either direction, ask the user which side is canonical.** Don't silently rewrite the docs to match disk, and don't move folders to match the docs. Both are plausible intents.

## Two-layer model: shared vs. personal

- Everything outside `.personal/` is **shared** reference material — factual content that benefits everyone (book overviews, key verses, cross-references, people, places, timelines). Changes go through PRs.
- `.personal/` is for the user's private study notes — reflections, prayers, journal entries, sermon notes. The `CONTRIBUTING.md` rule: if it's a fact, it's shared; if it's *your thought*, it's personal.

**Caveat on `.gitignore`:** line 3 (`#.personal/`) is currently **commented out**, even though `README.md` and `CONTRIBUTING.md` state `.personal/` is gitignored and never pushed. The `.personal/` directory currently contains tracked content (`README.md`, `Isaiah/`). If a task involves staging changes, do not assume `.personal/` is excluded — check `git status` and stage explicit paths rather than `git add -A`.

## Naming conventions

- **Book folders:** `NN-BookName`, zero-padded — `01-Genesis`, `46-1-Corinthians`, `66-Revelation`. Full list in `STRUCTURE.md` (uses old `books-of-bible/` paths but the `NN-BookName` names are correct).
- **Chapter folders:** `BookName-NN`, zero-padded — `Genesis-01`, `Psalms-119`, `Revelation-22`.
- **Every folder has exactly one `README.md`.** Additional files (images, attachments) may sit alongside.
- **Counts to preserve:** 66 books, 1,189 chapter folders.

## Chapter README format

Defined in `README-TEMPLATE.md`: `# [Book] [Chapter]` heading, then sections **Key Verses**, **Summary**, **Notes**, **Cross References**, **Questions**. Most chapter READMEs in `scripture/` are still stub `# Read Me` placeholders waiting to be filled in. Book-level READMEs (e.g., `scripture/01-Genesis/README.md`) follow a different format with Overview / Author / Date Written / Chapters / Key Themes.

When filling chapter content: factual, reference-quality, study-Bible-margin tone. `CONTRIBUTING.md` explicitly excludes denominational/doctrinal commentary and content from copyrighted translations from the shared layer.

## Specialized agents

Two tiers of subagents are committed under `.claude/agents/` and load automatically. Use them via the Agent tool when work matches their specialization.

**Research / theology agents** (output for the shared repo):

- `exegete` — single-passage close reading; chapter-README content
- `theologian` — systematic / biblical theology; topical studies
- `linguist` — Hebrew / Greek word studies
- `historian` — ANE / Second Temple / Greco-Roman background
- `geographer` — places, regions, routes
- `biographer` — biblical figures, church history, modern scholars
- `cross-references` — citations, allusions, parallels, typology

**Teacher-voice agents** (devotional output, usually for `.personal/`) — apply a specific teacher's hermeneutical lens without impersonating them:

- `teacher-perry-stone` — Hebrew roots, festival typology, prophetic patterns
- `teacher-chuck-missler` — integrated message system, typology, Christ-types
- `teacher-john-barnett` — verse-by-verse, dispensational, pre-trib
- `teacher-jonathan-cahn` — Hebrew word studies, prophetic parallels, Shemitah
- `teacher-john-bevere` — fear of the Lord, Day of the Lord, wrath vs tribulation
- `teacher-bill-creasy` — Bible as unified literary work, genre, geography

The teacher-voice agents pair with the `deep-bible-study-devotional` skill in `.claude/skills/`, which provides the devotional output structure.

See `.claude/agents/README.md` for how the agents divide labor and `.claude/agents/TEACHERS.md` for teacher-pairing suggestions. Each agent is told to read this CLAUDE.md before producing output, so updates here propagate.

## AI-Chats protocol

`.ai-chats/README.md` documents a self-imposed session-logging protocol (v3.2) the user actively maintains. Key rules:

- Each session is a folder `YYYY-MM-DD-NN-kebab-description/` (e.g., `2026-01-31-04-template-completion/`).
- Files inside follow `[Model-Version]--NN.md` — **no spaces, double-dash before sequence**. Example for this Claude Code session: `Opus-4.7--00.md`.
- `--00.md` is the main doc (summary, tech, lessons). `--01`, `--02`, ... are verbatim exchanges.
- `.ai-chats/INDEX.md` is the master index and must be updated when sessions are added.
- Only create/update these files when explicitly asked, or when the user is clearly continuing an existing session — don't auto-spawn them on every interaction.

## Things to avoid

- Don't run `git add -A` / `git add .` — `.gitignore` doesn't currently exclude `.personal/`, so a wildcard add can leak private notes into a commit. Stage explicit paths.
- Don't invent build/test/lint commands. There is no toolchain here.
- Don't fill chapter content with sermon-style or denominational commentary — that belongs in `.personal/`, not the shared repo.
- Don't reconcile the docs-vs-disk inconsistency without asking which side is canonical.
