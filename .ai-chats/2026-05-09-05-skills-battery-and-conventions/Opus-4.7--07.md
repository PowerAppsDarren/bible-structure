# Exchange 07 — Underscore prefix convention + docs propagation + memory

- **Timestamp:** 2026-05-09
- **Context:** The user established a durable convention for distinguishing custom-built skills/commands from third-party bundles like GSD, then immediately asked it be both documented in CLAUDE.md and saved as memory.

## User Input — First prompt

```
all skills and commands we create together should always be prefixed with `_` so I can see all the ones we've created. as opposed to the gsd skills, for example
```

## User Input — Two interrupt-style follow-ups during my work

```
add this to the repo's CLAUDE.md pls
```

```
aka: remember this convension
```

## Reasoning Path

Two parts:

1. **Apply the prefix to existing skills** — all 11 (10 new + the existing `deep-bible-study-devotional`). The existing one is "ours together" too even though it came from a parallel session; only third-party bundles should remain unprefixed. Agents are explicitly NOT prefixed (the user said "skills and commands").

2. **Make the convention sticky** — document in CLAUDE.md (in-repo for any user/Claude reading the repo) AND save as a feedback memory in the per-project memory store (auto-loaded by future Claude Code sessions in this project).

Bulk replace strategy: PowerShell loop renaming 11 folders, then a content pass with regex `(?<!_)\b<skill-name>\b` → `_<skill-name>` to (a) match whole skill names with word boundaries, (b) skip names already prefixed (negative lookbehind), and (c) handle hyphens correctly.

## Tool Calls (manifest)

**Phase 1 — bulk rename + content propagation:**
- One PowerShell script: rename 11 skill folders + regex-replace skill names in 16 files (`.claude/skills/**/*.{md,html}`, `.claude/agents/*.md`, `CLAUDE.md`).
- The regex caught two prose false positives in `.claude/agents/README.md` ("Building word-study notes" and "doesn't write the word-study itself" — generic prose, not skill name references).

**Phase 2 — memory + docs (after the user's two follow-up prompts):**
- `Write` of feedback memory at `~/.claude/projects/C--Users-DarrenNeese-src-bible-structure/memory/feedback_skill-and-command-naming.md`.
- `Grep` to find any other prose false positives — confirmed only the two known issues in `agents/README.md` plus correct uses (`_deep-bible-study-devotional` references in `agents/README.md` line 30 and `TEACHERS.md` line 56, which were correct since they are skill name references).
- `Bash ls` of the memory directory to check for an existing `MEMORY.md` index — none, only the feedback file just created.
- Four parallel `Edit`s:
  - `.claude/agents/README.md` line 11 (revert false positive: `_word-study` → `word-study`)
  - `.claude/agents/README.md` line 47 (revert false positive: `_word-study` → `word study`)
  - `CLAUDE.md` (add "Naming convention — underscore prefix" sub-section in Skills section)
  - `.claude/skills/README.md` (add convention to "Adding a new skill" section)
- One `Write` of `MEMORY.md` index file pointing to the feedback memory.

## My Visible Response (final summary — verbatim closing)

> All set. Summary of this round:
>
> - **11 skills renamed** to `_<name>/` (the 10 we just built + the existing `deep-bible-study-devotional`). Folder names + `name:` frontmatter + cross-references all in sync.
> - **Convention documented in `CLAUDE.md`** under Skills as a sub-section, with explicit guidance that agents do NOT get the prefix.
> - **Convention also in `.claude/skills/README.md`** under "Adding a new skill" so anyone scaffolding a new skill from that doc sees the rule.
> - **Two prose false-positives reverted** in `agents/README.md` (generic "word-study" mentions that got incorrectly prefixed).
> - **Memory saved** to `~/.claude/projects/C--Users-DarrenNeese-src-bible-structure/memory/feedback_skill-and-command-naming.md` with `MEMORY.md` index entry. Future Claude Code sessions in this repo will automatically apply the convention.

## Files Read / Modified

| Action | Files |
|--------|-------|
| Renamed (folders) | 11 skills: `<name>/` → `_<name>/` |
| Content updated by bulk script | 16 files (`.claude/skills/**`, `.claude/agents/*.md`, `CLAUDE.md`) |
| Reverted false positives | `.claude/agents/README.md` (2 lines) |
| New convention docs | `CLAUDE.md` (Skills sub-section); `.claude/skills/README.md` ("Adding a new skill") |
| New memory | `~/.claude/projects/C--Users-DarrenNeese-src-bible-structure/memory/feedback_skill-and-command-naming.md`; `MEMORY.md` index |

## Outcome

Final skills folder, alphabetical:

```
.claude/skills/
├── README.md                          (admin)
├── _chapter-readme-fill/
├── _character-study/
├── _compare-notes/
├── _cross-reference-map/
├── _deep-bible-study-devotional/
├── _group-discussion-prep/
├── _personal-reflection/
├── _place-study/
├── _prayer-from-passage/
├── _topic-trace/
└── _word-study/
```

Future Claude Code sessions in this repo will read the saved memory automatically and apply the `_` prefix when creating any new custom skill or command without needing to re-explain.
