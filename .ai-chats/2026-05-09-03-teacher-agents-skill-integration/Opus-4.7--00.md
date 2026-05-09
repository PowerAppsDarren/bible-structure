# AI Chat Session: Teacher-Voice Agents & Deep-Bible-Study Skill Integration

- **Date:** 2026-05-09
- **Model:** Claude Opus 4.7 (1M context)
- **Topic:** Integrate six teacher-voice subagents and the `deep-bible-study-devotional` skill from an external OneDrive bundle into the bible-structure repo
- **Tool:** Claude Code
- **Project:** bible-structure
- **Exchange Count:** 1

## 💡 Conversation Summary

User asked to integrate the contents of `C:\Users\DarrenNeese\OneDrive - Super Power Labs\src\26-05-09--bible-study` into the repo. The bundle contained:

- Six Bible-teacher subagent markdown files (Perry Stone, Chuck Missler, John Barnett, Jonathan Cahn, John Bevere, Bill Creasy)
- A `README.md` describing those agents and pairing suggestions
- `deep-bible-study-devotional.skill` — an OOXML/zip-packaged Claude skill
- `deep-bible-study-skill-overview.html` — overview HTML for the skill

Plan executed:

1. Copied the 6 teacher agents to `.claude/agents/`.
2. Renamed the bundle's `README.md` to `.claude/agents/TEACHERS.md` to avoid colliding with the existing agents `README.md`.
3. Extracted the `.skill` zip and copied its contents into `.claude/skills/deep-bible-study-devotional/` (created `.claude/skills/` since it did not exist).
4. Placed `deep-bible-study-skill-overview.html` next to the skill as `overview.html`.
5. Updated `.claude/agents/README.md` with a new "Teacher-voice agents" table and a note that their devotional output usually belongs in `.personal/`.
6. Updated root `CLAUDE.md` "Specialized agents" section to split into research vs. teacher-voice tiers and point at the new skill.

Outcome: 13 agents now load from `.claude/agents/`. The `deep-bible-study-devotional` skill is registered (visible in the skills list shown to Claude this session).

## 🔧 Technical Details

**Files added:**

- `.claude/agents/perry-stone.md`
- `.claude/agents/chuck-missler.md`
- `.claude/agents/john-barnett.md`
- `.claude/agents/jonathan-cahn.md`
- `.claude/agents/john-bevere.md`
- `.claude/agents/bill-creasy.md`
- `.claude/agents/TEACHERS.md`
- `.claude/skills/deep-bible-study-devotional/SKILL.md`
- `.claude/skills/deep-bible-study-devotional/references/pushback-patterns.md`
- `.claude/skills/deep-bible-study-devotional/references/output-template.md`
- `.claude/skills/deep-bible-study-devotional/references/eden-directives-framework.md`
- `.claude/skills/deep-bible-study-devotional/references/trusted-teachers.md`
- `.claude/skills/deep-bible-study-devotional/assets/example-isaiah-1.md`
- `.claude/skills/deep-bible-study-devotional/overview.html`

**Files modified:**

- `.claude/agents/README.md` — added Teacher-voice tier table + softened "all seven" wording
- `CLAUDE.md` — split agent listing into two tiers and added skill pointer

**Tools/commands:**

- `unzip` to extract the `.skill` OOXML bundle into `/tmp/skill-extract/`
- `cp` (Bash via Git Bash) for the copy operations
- `Edit` on the two markdown docs

**Not done (deliberately):**

- No git staging / commit. Repo rule is "never `git add -A`" because `.gitignore` line 3 has `.personal/` commented out. User to stage explicit paths and commit when ready.

## 📚 Lessons Learned

- The `.skill` extension is just an OOXML/zip container. `unzip` worked directly without renaming.
- `.claude/skills/` did not exist in the repo previously; creating it under `.claude/` is the standard Claude Code location for project-scoped skills, and it was picked up immediately (the skill appeared in the next system-reminder skill listing).
- The bundle's `README.md` would have shadowed the existing agents `README.md` if dropped at the root of `.claude/agents/`. Renamed to `TEACHERS.md` to preserve both.
- Confirmed the existing CLAUDE.md "seven research agents" framing needed updating once a second tier landed — keeping CLAUDE.md authoritative is important since every agent reads it.

## ⏭️ Next Steps

- User to review `git status` and stage explicit paths for commit (do **not** use `git add -A` — `.personal/` is currently un-ignored).
- Optional: add a short note in `CONTRIBUTING.md` clarifying that teacher-voice devotional output belongs in `.personal/`, not the shared layer.
- Optional: try the skill on a chapter (e.g., Isaiah 1, which has an example asset already shipped in the skill).

## 📁 Exchange Index

- [01 — Integrate OneDrive bible-study bundle](./Opus-4.7--01.md)
