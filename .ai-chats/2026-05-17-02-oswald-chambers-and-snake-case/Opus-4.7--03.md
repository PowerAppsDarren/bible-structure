# Exchange 03: Snake_case rename + update the meta-skill

- **Timestamp:** 2026-05-17
- **Context:** User wants the new skill (and all custom skills) renamed to snake_case.

## User Input

> make it snake  cased

(Followed by an `AskUserQuestion` clarifying scope; user selected the third option with a custom note. Then a follow-up message:)

> update your skill creation skill for this

User's AskUserQuestion answer text: *"snake case skills and prefix with underscore... skills you and I create together"*

## AI Response

Quick clarification before I rename anything — every existing file in `.claude/agents/` and `.claude/skills/` is **kebab-case** (`teacher-bill-creasy`, `_word-study`), which is also what Claude Code's skill/agent loader expects for the `name:` field.

True snake_case (`teacher_oswald_chambers`, `_new_teacher_agent`) would:
- Diverge from all 7 other teacher agents and all 13 existing skills
- Require the `name:` frontmatter field to also be snake_case (skill/agent names must match the folder/file)
- Break the convention documented in `CLAUDE.md` ("Prefix the folder/file name with `_`" — the rest is kebab)

Which did you mean?

(AskUserQuestion presented 3 scope options. User answered: "snake case skills and prefix with underscore... skills you and I create together.")

Understood — switching the custom-skills convention from `_kebab-case` to `_snake_case`. Agents stay kebab-case as-is.

Let me confirm scope before I move 12 folders and update all the cross-references. I'll do this in waves:

1. Rename all `_kebab-case` skill folders → `_snake_case`
2. Update each `SKILL.md` `name:` frontmatter to match
3. Update `CLAUDE.md`, `.claude/skills/README.md`, `.claude/agents/README.md`, `.claude/agents/TEACHERS.md`
4. Fix cross-skill references (skills reference each other by name)

Let me check what needs renaming and where they're cross-referenced.

(Ran PowerShell `git mv` loop. 11 of 12 succeeded. `_new-teacher-agent` failed because the directory was uncommitted/untracked.)

11/12 succeeded. The new uncommitted `_new-teacher-agent` needs a plain rename, then I'll batch-update all the `name:` frontmatter fields and cross-references.

(Ran plain `mv` for the last one; confirmed all 12 folders now in snake_case form. Then ran a single PowerShell batch find-and-replace across 17 files using a hashtable of 12 token pairs.)

Acknowledged. I'll do both in one pass: rename + update the skill-creation skill (`_new-teacher-agent` → `_new_teacher_agent`) so its own instructions teach the new snake_case convention going forward.

Renaming all 12 folders first.

(Then, after rename + batch replace:)

All folder + file references updated. Now I need to make the convention **explicitly snake_case** in three places (the docs currently say "underscore prefix" without specifying the rest), and update `_new_teacher_agent` to teach the new convention.

(Edited `CLAUDE.md` "Naming convention" section to spell out: `_snake_case` for skills/commands, `kebab-case` for agents, don't mix. Edited `.claude/skills/README.md` "Adding a new skill" section to match. Edited `.claude/skills/_new_teacher_agent/SKILL.md` to clarify that agents stay kebab-case and to point back to CLAUDE.md for the skill convention.)

End-of-turn summary:

Clean. The only remaining `_kebab-case` strings are references to the planning doc `____bible-study-top-level-folders.md`, which isn't a skill.

**Summary of changes:**

- **12 skill folders renamed** from `_kebab-case` → `_snake_case` (11 via `git mv` preserving history; `_new_teacher_agent` via plain `mv` since it was uncommitted).
- **17 files updated** with global find-and-replace: every `SKILL.md` frontmatter `name:` field, every cross-skill reference inside skills, `CLAUDE.md`, `.claude/skills/README.md`, `.claude/agents/README.md`, `.claude/agents/TEACHERS.md`, and `overview.html`.
- **Convention now explicit in three places:**
  - `CLAUDE.md` — rewrote the "Naming convention" section to spell out: `_snake_case` for skills/commands, `kebab-case` for agents, don't mix.
  - `.claude/skills/README.md` — rewrote the "Adding a new skill" section to match.
  - `.claude/skills/_new_teacher_agent/SKILL.md` — clarified that agents stay kebab-case and pointed back to `CLAUDE.md` for the skill convention, so future teacher-agent creation enforces both rules.

Skill list now shows all 12 in snake_case (`_word_study`, `_chapter_readme_fill`, `_new_teacher_agent`, etc.). The Oswald Chambers agent is in place. No commit made — let me know when you want one.

## Tool Calls

- `AskUserQuestion`: 1 question, 3 scope options
- `Bash`: `ls .claude/skills/` — listed 13 entries (12 `_kebab-case` skill folders + README.md)
- `Grep` (×3): scanned `.claude` and root for `_[a-z]+-[a-z-]+` patterns + backticked skill references → 17 files affected
- `PowerShell` (×3): folder rename loop using `git mv` (11 successful); plain `mv` for the uncommitted folder; global find-and-replace using `$pairs` hashtable across 17 files
- `Bash`: `git status --short` + `ls .claude/skills/` after rename — confirmed 11 R (rename) entries + 1 untracked `_new-teacher-agent/`
- `Read` (×3): `.claude/skills/README.md`, `CLAUDE.md` (offset 96), `.claude/skills/_new_teacher_agent/SKILL.md` (first 30 lines)
- `Edit` (×3): `CLAUDE.md` naming-convention section; `.claude/skills/README.md` "Adding a new skill" section; `_new_teacher_agent/SKILL.md` agent-vs-skill clarification
- `Grep` (final verification): pattern `_[a-z]+-[a-z][a-z-]+` against `.claude/` and `CLAUDE.md` → only matches were references to the planning doc filename, not skills

## Function Results

PowerShell `git mv` loop output (key line):

```
fatal: source directory is empty, source=.claude/skills/_new-teacher-agent, destination=.claude/skills/_new_teacher_agent
```

(11 silent successes preceded this; failure was the still-uncommitted folder.)

PowerShell batch find-and-replace output:

```
updated: CLAUDE.md
updated: .claude/skills/README.md
updated: .claude/agents/README.md
updated: .claude/agents/TEACHERS.md
updated: .claude/skills/_chapter_readme_fill/SKILL.md
updated: .claude/skills/_character_study/SKILL.md
updated: .claude/skills/_compare_notes/SKILL.md
updated: .claude/skills/_cross_reference_map/SKILL.md
updated: .claude/skills/_deep_bible_study_devotional/SKILL.md
updated: .claude/skills/_deep_bible_study_devotional/overview.html
updated: .claude/skills/_group_discussion_prep/SKILL.md
updated: .claude/skills/_new_teacher_agent/SKILL.md
updated: .claude/skills/_personal_reflection/SKILL.md
updated: .claude/skills/_place_study/SKILL.md
updated: .claude/skills/_prayer_from_passage/SKILL.md
updated: .claude/skills/_topic_trace/SKILL.md
updated: .claude/skills/_word_study/SKILL.md
```

Final verification Grep output: only 2 hits, both for `____bible-study-top-level-folders.md` (planning doc filename, unrelated to skills).

## Files Read/Modified

**Folders renamed (12):**
All `.claude/skills/_<old>` → `.claude/skills/_<snake_case>`

**Files modified (17, all via batch replace + 3 targeted edits):**
- `CLAUDE.md` (batch + targeted edit to naming-convention section)
- `.claude/skills/README.md` (batch + targeted edit to "Adding a new skill")
- `.claude/agents/README.md` (batch)
- `.claude/agents/TEACHERS.md` (batch)
- All 12 `SKILL.md` files (batch)
- `.claude/skills/_deep_bible_study_devotional/overview.html` (batch)
- `.claude/skills/_new_teacher_agent/SKILL.md` (batch + targeted edit clarifying agent-vs-skill conventions)
