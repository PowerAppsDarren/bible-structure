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

## Two-layer model: shared vs. shared-personal (multi-user)

The repo is designed for small-group / church use. Two layers:

- **Shared layer** — everything outside `.personal/` (`scripture/`, `topics/`, `words/`, `people/`, `places/`, `theology/`, etc.). Factual reference material that benefits everyone, changed via PR.
- **Shared-personal layer** — `.personal/<user-email>/`: each user has a folder named by their email address (e.g., `.personal/darren@neese.us/`). Personal reflections, journals, prayer notes, teaching prep. The folder is **intentionally tracked in git** (not gitignored). Members share by pushing; privacy is by convention. See `.personal/README.md`.

`CONTRIBUTING.md` rule: fact = shared; *your thought* = `.personal/<your-email>/`. Never write inside another user's email folder — that space is read-only by convention.

**Two stale claims in older docs:**
- `README.md`, `CONTRIBUTING.md`, and `CHANGELOG.md` 1.2.0 still describe `.personal/` as "gitignored, never pushed" — that's the old single-user paradigm. The multi-user paradigm above supersedes it. The `.gitignore` correctly does NOT exclude `.personal/`.
- The published structure docs still describe `books-of-bible/` and `topics-of-study/` (see "Layout on disk vs. layout in the docs" above).

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

The teacher-voice agents pair with the `_deep-bible-study-devotional` skill in `.claude/skills/`, which provides the devotional output structure.

See `.claude/agents/README.md` for how the agents divide labor and `.claude/agents/TEACHERS.md` for teacher-pairing suggestions. Each agent is told to read this CLAUDE.md before producing output, so updates here propagate.

## Skills

A coordinated battery of skills under `.claude/skills/` covers the four phases of small-group Bible study. Skills are **model-invoked** (Claude decides when to fire based on the user's message); user-typed shortcuts go in `.claude/commands/` (not yet present).

- **Heavyweight chapter walk:** `_deep-bible-study-devotional`
- **Research:** `_word-study`, `_cross-reference-map`, `_character-study`, `_place-study`, `_topic-trace`
- **Group:** `_group-discussion-prep`, `_compare-notes` (multi-user — reads across `.personal/*/`)
- **Personal:** `_personal-reflection`, `_prayer-from-passage` (write to `.personal/<email>/` only)
- **Maintenance:** `_chapter-readme-fill` (writes to shared `scripture/`)

See `.claude/skills/README.md` for how skills compose with each other and with the agents. Skills enforce the two-layer discipline: shared output goes to top-level folders; personal output stays inside the user's email folder.

### Naming convention — underscore prefix on custom skills and commands

All custom skills and slash commands we create together for this repo are prefixed with `_` (e.g., `_word-study`, `_chapter-readme-fill`). This visually distinguishes them from third-party skill bundles (GSD and similar) at a glance — anything starting with `_` in `.claude/skills/` or `.claude/commands/` is something built specifically for this repo.

When adding a new skill or command:
- Prefix the folder/file name with `_` (`.claude/skills/_<name>/SKILL.md`, `.claude/commands/_<name>.md`).
- Set `name: _<name>` in the YAML frontmatter so it matches.
- Update references in this `CLAUDE.md`, `.claude/skills/README.md`, and any cross-references between skills.

**Agents do NOT get the prefix** — the convention is skills/commands only. Agent files stay as `exegete.md`, `theologian.md`, `teacher-perry-stone.md`, etc.

## AI-Chats protocol

`.ai-chats/README.md` documents a self-imposed session-logging protocol (v3.2) the user actively maintains. Key rules:

- Each session is a folder `YYYY-MM-DD-NN-kebab-description/` (e.g., `2026-01-31-04-template-completion/`).
- Files inside follow `[Model-Version]--NN.md` — **no spaces, double-dash before sequence**. Example for this Claude Code session: `Opus-4.7--00.md`.
- `--00.md` is the main doc (summary, tech, lessons). `--01`, `--02`, ... are verbatim exchanges.
- `.ai-chats/INDEX.md` is the master index and must be updated when sessions are added.
- Only create/update these files when explicitly asked, or when the user is clearly continuing an existing session — don't auto-spawn them on every interaction.

## Things to avoid

- **Never write inside another user's `.personal/<email>/` folder.** Each user owns their own. Other users' folders are read-only by convention.
- Don't `git add -A` paths outside the user's own email folder unless intentionally PR-ing shared content. The intentional-tracking of `.personal/` makes wildcard adds safer than they were under the old paradigm, but staying scoped is still good hygiene.
- Don't invent build/test/lint commands. There is no toolchain here.
- Don't fill chapter content with sermon-style or denominational commentary — that belongs in `.personal/<your-email>/`, not the shared repo.
- Don't reconcile the docs-vs-disk inconsistency without asking which side is canonical.
