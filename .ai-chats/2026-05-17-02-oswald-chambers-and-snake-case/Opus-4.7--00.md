# AI Chat Session: Oswald Chambers Teacher Agent + Snake_Case Skill Convention

- **Date:** 2026-05-17
- **Model:** Claude Opus 4.7 (1M context) — `claude-opus-4-7[1m]`
- **Topic:** Add Oswald Chambers as the 7th teacher-voice agent, build a project-only meta-skill for scaffolding future teacher agents, then rename all 12 custom skills from `_kebab-case` to `_snake_case` and update every cross-reference
- **Tool:** Claude Code
- **Project:** bible-study (`C:\Users\DarrenNeese\src\bible-study`)
- **Exchange Count:** 5

## 💡 Conversation Summary

User asked to create a new teacher-voice agent for Oswald Chambers, matching the pattern of the six existing teacher agents in `.claude/agents/`. After confirming there was no existing skill that scaffolds teacher agents, the user requested both: the new Chambers agent AND a project-only meta-skill (`_new_teacher_agent`) for scaffolding future teacher agents.

After both were created, the user asked to convert all custom skills from `_kebab-case` to `_snake_case`. The agents stay kebab-case (per the existing convention); only the `_`-prefixed custom skills switch to snake_case. This required:

1. Renaming 12 skill folders (11 via `git mv` preserving history; 1 via plain `mv` since uncommitted)
2. Updating each `SKILL.md`'s `name:` frontmatter field
3. Updating every cross-skill reference inside SKILL.md files
4. Rewriting the naming-convention sections in `CLAUDE.md` and `.claude/skills/README.md` to explicitly state `_snake_case` for skills + `kebab-case` for agents
5. Updating the `_new_teacher_agent` skill itself to teach the new convention

User then asked whether Oswald was "added as a teacher" — discovered he was missing from `_deep_bible_study_devotional`'s trigger description and `references/trusted-teachers.md`. Added him there too.

Net outcome: 7 teacher agents (was 6), 12 `_snake_case` skills (was 12 `_kebab-case`), naming conventions explicit, Chambers fully integrated into the devotional skill's citation library.

## 🔧 Technical Details

**Files created:**
- `.claude/agents/teacher-oswald-chambers.md` — new agent file (~3.3 KB) with frontmatter, hermeneutical lens, voice, emphases, citation patterns, conviction-at-center
- `.claude/skills/_new_teacher_agent/SKILL.md` — project-only meta-skill for scaffolding future teacher agents (originally created as `_new-teacher-agent`, renamed in step 2)

**Files renamed (12 folders, `_kebab-case` → `_snake_case`):**
- `_chapter-readme-fill` → `_chapter_readme_fill`
- `_character-study` → `_character_study`
- `_compare-notes` → `_compare_notes`
- `_cross-reference-map` → `_cross_reference_map`
- `_deep-bible-study-devotional` → `_deep_bible_study_devotional`
- `_group-discussion-prep` → `_group_discussion_prep`
- `_new-teacher-agent` → `_new_teacher_agent`
- `_personal-reflection` → `_personal_reflection`
- `_place-study` → `_place_study`
- `_prayer-from-passage` → `_prayer_from_passage`
- `_topic-trace` → `_topic_trace`
- `_word-study` → `_word_study`

11 of 12 renamed via `git mv` (preserves history); `_new-teacher-agent` renamed via plain `mv` because it was uncommitted at the time.

**Files modified (find-and-replace + targeted edits):**
- `CLAUDE.md` — Chambers added to "Teacher-voice agents" list; "Naming convention" section rewritten to explicitly say `_snake_case` for skills/commands, `kebab-case` for agents
- `.claude/skills/README.md` — "Adding a new skill" section rewritten; one Maintenance-table row added for `_new_teacher_agent`; all skill references updated to snake_case
- `.claude/agents/README.md` — skill references updated
- `.claude/agents/TEACHERS.md` — count "six" → "seven"; Chambers row added to agent table; skill reference updated
- 12 `SKILL.md` files — `name:` frontmatter snake_cased; cross-skill references updated
- `.claude/skills/_deep_bible_study_devotional/overview.html` — skill name reference updated
- `.claude/skills/_deep_bible_study_devotional/SKILL.md` — Chambers added to teacher-name trigger list
- `.claude/skills/_deep_bible_study_devotional/references/trusted-teachers.md` — full Chambers citation profile added; "Match the teacher to the moment" rule expanded
- `.claude/skills/_new_teacher_agent/SKILL.md` — naming-convention note clarified (agents kebab, skills snake)

**Tools/commands used:**
- `git mv` for 11 of 12 folder renames (preserves history)
- PowerShell batch script (single command) for the global find-and-replace across 17 files using a hashtable of 12 token pairs
- `Read`/`Edit`/`Write` for targeted content edits
- `Grep` to verify no stale `_kebab-case` references remained
- `Glob` and `Bash ls` for filesystem enumeration
- No commits made — user has not yet requested one

## 📚 Lessons Learned

- **`git mv` requires the source to be tracked.** The just-created `_new-teacher-agent` folder was uncommitted, so `git mv` failed with "fatal: source directory is empty"; recovered with plain `mv`. Lesson: stage new folders before renames if you want full history preservation.
- **The convention rename has two halves: filenames and `name:` frontmatter.** Both must match exactly for Claude Code's skill loader to register the skill. A batch find-and-replace across all `SKILL.md` files is the right move; the post-rename system reminder confirmed the registry picked up all 12 new snake_case names.
- **Adding a teacher takes 5 places, not 3.** First pass only updated the agent file + `TEACHERS.md` + `CLAUDE.md`. User caught that the devotional skill's trigger list and `trusted-teachers.md` citation library still listed only six teachers. Future `_new_teacher_agent` runs need to include these two places in their workflow.
- **PowerShell hashtable-driven find-and-replace is reliable for batch token swaps** when the token list is small and unambiguous. Pattern: `Get-Content -Raw` → loop `.Replace()` for each pair → `Set-Content -NoNewline -Encoding utf8`.
- **A "snake_case" instruction in this repo is unambiguous.** The user previously approved kebab-case for both agents and skills; the new instruction (skills snake_case, agents kebab-case) is a deliberate divergence to visually distinguish skill identifiers from agent identifiers at a glance. Documenting *why* the two conventions differ matters more than the rename itself.

## ⏭️ Next Steps

- **Commit the changes.** Nothing is staged or committed yet. User asked for the rename but hasn't asked to commit. The new tree state is:
  - 1 new agent file (`teacher-oswald-chambers.md`)
  - 1 new skill folder (`_new_teacher_agent/`)
  - 12 skill folder renames (11 detected by git as renames; 1 untracked-add)
  - Modifications to `CLAUDE.md`, `.claude/skills/README.md`, `.claude/agents/README.md`, `.claude/agents/TEACHERS.md`, and 12 `SKILL.md` files plus 1 `overview.html` plus `references/trusted-teachers.md`
- **Smoke-test the `_new_teacher_agent` skill** on a hypothetical next teacher (Spurgeon? Tozer? Lewis? Ravi Zacharias?) to verify the workflow + indexes-to-update list is correct.
- **Consider a similar rename for `.ai-chats/` filenames?** The AI-Chats protocol uses `Opus-4.7--NN.md` (kebab + double-dash + sequence). Not affected by this rename — that convention is independent.

## 📁 Exchange Index

- [01 — Create Oswald Chambers agent (and check if a scaffolding skill exists)](./Opus-4.7--01.md)
- [02 — Build Chambers agent + project-only meta-skill](./Opus-4.7--02.md)
- [03 — Snake_case rename + update the meta-skill](./Opus-4.7--03.md)
- [04 — Confirm Oswald is fully registered as a teacher](./Opus-4.7--04.md)
- [05 — Wrap up per AI-Chats Protocol v3.2](./Opus-4.7--05.md)
