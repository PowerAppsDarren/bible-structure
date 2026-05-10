# AI Chat Session: Skills battery, multi-user paradigm, and naming conventions

- **Date:** 2026-05-09
- **Model:** Opus-4.7 (1M context)
- **Topic:** Continuing from session 02. Two passes of teacher-agent renames, aggressive shortening of research agent names, scoping clarification (this repo vs. coding repos), 10-skill battery built under `.claude/skills/`, multi-user `.personal/<user-email>/` paradigm with documentation reset, and an underscore-prefix convention for custom skills/commands committed to durable memory.
- **Tool:** Claude Code
- **Project:** bible-structure
- **Exchange Count:** 7 substantive + this logging exchange

## Conversation Summary

After session 02 (CLAUDE.md + 7 research agents) wrapped, the parallel session 03 had landed six teacher-voice agents, a `deep-bible-study-devotional` skill, plus modifications to `CLAUDE.md` and `.claude/agents/README.md`. This session picked up from there and did substantial reorganization plus expansion across seven user-driven turns.

The thread:

1. **Reconciled the parallel-session changes** by updating the postscript of session 02's `--05.md` to note that the teacher-voice work had been logged at session 03.

2. **Renamed teacher agents — twice.** First lengthened (`perry-stone.md` → `bible-teacher-perry-stone.md`) to make the filenames match the `name:` frontmatter. The user then pushed back ("i hate long file names"), so I removed the `bible-teacher-` prefix entirely. The user clarified the actual goal — they wanted teachers grouped together in directory listings — so the final form became `teacher-perry-stone.md` (prefix kept, just shorter).

3. **Aggressively shortened the research agent names** in the same pass: `scripture-exegete → exegete`, `biblical-theologian → theologian`, `hebrew-greek-linguist → linguist`, `biblical-historian → historian`, `biblical-geographer → geographer`, `biographical-researcher → biographer`, `cross-reference-curator → cross-references`. Done via a single PowerShell script that handled file renames, frontmatter updates, and cross-references in CLAUDE.md and the agents README in one pass.

4. **Answered a scoping question** ("is this repo different, right? we wouldn't want to store/use this stuff for our coding repos, right?"). Confirmed: yes, project-scoped only. Documented project `.claude/` vs user-global `~/.claude/` resolution.

5. **Explained skills vs commands.** Skills are model-invoked (Claude decides when to fire); commands are user-invoked (typeable shortcuts). Complementary, not redundant.

6. **Built a 10-skill battery** under `.claude/skills/`:
   - Research: `word-study`, `cross-reference-map`, `character-study`, `place-study`, `topic-trace`
   - Group: `group-discussion-prep`, `compare-notes`
   - Personal: `personal-reflection`, `prayer-from-passage`
   - Maintenance: `chapter-readme-fill`
   - Plus a battery README documenting how skills compose with each other and with the agents.

7. **Documented and propagated the multi-user `.personal/<email>/` paradigm.** Each user has a folder named by their email address under `.personal/`; the folder is intentionally tracked in git; sharing is by push/pull and privacy is by convention. Updated `CLAUDE.md`, rewrote `.personal/README.md`, and corrected the misleading `#.personal/` comment in `.gitignore`.

8. **Applied a `_` prefix to all 11 skills** (10 new + the existing `_deep-bible-study-devotional`) so custom skills visually separate from third-party bundles like GSD. The convention is documented in CLAUDE.md and `.claude/skills/README.md`, and saved as a durable feedback memory at `~/.claude/projects/.../memory/feedback_skill-and-command-naming.md` (with `MEMORY.md` index entry) so future sessions automatically apply it.

## Technical Details

### Files created

**Skills (each is a folder with SKILL.md):**
- `.claude/skills/_word-study/`
- `.claude/skills/_cross-reference-map/`
- `.claude/skills/_character-study/`
- `.claude/skills/_place-study/`
- `.claude/skills/_topic-trace/`
- `.claude/skills/_group-discussion-prep/`
- `.claude/skills/_compare-notes/`
- `.claude/skills/_personal-reflection/`
- `.claude/skills/_prayer-from-passage/`
- `.claude/skills/_chapter-readme-fill/`
- `.claude/skills/README.md` (battery overview)

**Memory:**
- `~/.claude/projects/C--Users-DarrenNeese-src-bible-structure/memory/feedback_skill-and-command-naming.md`
- `~/.claude/projects/C--Users-DarrenNeese-src-bible-structure/memory/MEMORY.md`

### Files renamed

- **6 teacher agents** through three states: `<name>.md` → `bible-teacher-<name>.md` → `<name>.md` → `teacher-<name>.md`.
- **7 research agents** shortened: `scripture-exegete.md` → `exegete.md`; `biblical-theologian.md` → `theologian.md`; `hebrew-greek-linguist.md` → `linguist.md`; `biblical-historian.md` → `historian.md`; `biblical-geographer.md` → `geographer.md`; `biographical-researcher.md` → `biographer.md`; `cross-reference-curator.md` → `cross-references.md`.
- **11 skill folders** prefixed with `_`.

### Files modified

- `CLAUDE.md` — Multi-user `.personal/<email>/` two-layer section; new Skills section; `_` naming convention sub-section; "Things to avoid" updated; agent name updates from rename pass.
- `.gitignore` — Replaced misleading `#.personal/` line with clear convention comment.
- `.personal/README.md` — Rewrote to document the multi-user paradigm.
- `.claude/agents/README.md` — Agent name updates; reverted two false-positive `_word-study` prose mentions; one prose fix on the `cross-references` agent (added "agent" word for grammatical fit).
- `.claude/agents/TEACHERS.md` — Agent and skill name updates.
- `.ai-chats/2026-05-09-02-claude-md-and-agents/Opus-4.7--05.md` — Postscript updated to note session 03 covered the parallel work.

## Lessons Learned

- **The user values brevity AND grouping; trade-offs need to be surfaced.** Initial preference was "shorter is better"; after a re-think, they wanted a `teacher-` prefix back to keep the teacher agents visually grouped in directory listings. When offering rename options, present both axes (length, grouping) explicitly so the user doesn't have to iterate.
- **PowerShell bulk-replace is efficient for systematic renames but creates prose false positives.** Both rename passes introduced one or two awkward prose constructions (`The cross-references does Y` subject-verb mismatch from the `cross-reference-curator → cross-references` rename; generic "word-study" prose getting prefixed). Always follow up bulk renames with a targeted prose grep.
- **Project-scoped `.claude/` is the right safety mental model.** The user's question "is this repo different, right?" is exactly the check that prevents Bible-study agents from cluttering coding-repo registries. CLAUDE.md now documents this clearly.
- **Multi-user `.personal/<email>/` is a clean design** — small-group sharing without a permission system; privacy is by convention. The previously-confusing commented-out `.gitignore` line was always pointing toward this paradigm.
- **Skills and commands are complementary.** Worth having both: skills handle "Claude figures out the right time"; commands handle "I know exactly what I want, give me a typeable shortcut."
- **Underscore-prefix convention** is a memorable, low-friction way to distinguish custom from third-party `.claude/` content. Once saved as durable memory, it propagates without re-explaining.

## Next Steps

- `.claude/commands/` is still empty. The user may want a starter set of slash commands tied to the skills (`/_study`, `/_word`, `/_journal`, `/_fill-chapter`).
- The published `README.md`, `CONTRIBUTING.md`, and `CHANGELOG.md` 1.2.0 still describe `.personal/` as "gitignored, never pushed" (old single-user paradigm). Coordinated rewrite is pending user direction.
- The docs-vs-disk path inconsistency (`books-of-bible/` vs `scripture/`) is also still pending.
- `darren.md` was added to `.gitignore` mid-session by parallel work — apparently a temporary working file the user keeps locally. Worth knowing for context but no action needed.

## Exchange Files

- [01 — Post-02 cleanup of parallel session changes](./Opus-4.7--01.md)
- [02 — Teacher rename round 1: filename ↔ frontmatter mismatch fix (wrong direction)](./Opus-4.7--02.md)
- [03 — Scoping clarification: this repo vs. coding repos](./Opus-4.7--03.md)
- [04 — Full rename saga: bible-/teacher- adjustments + research aggressive shorten](./Opus-4.7--04.md)
- [05 — Skills vs commands conceptual question](./Opus-4.7--05.md)
- [06 — 10-skill battery + multi-user `.personal/<email>/` paradigm](./Opus-4.7--06.md)
- [07 — Underscore prefix convention + docs propagation + memory](./Opus-4.7--07.md)
- [08 — Full-protocol session logging](./Opus-4.7--08.md)

## Postscript — session number collision

This session was originally written into `2026-05-09-04-skills-battery-and-conventions/`, but a parallel Claude Code session had concurrently claimed slot 04 with `2026-05-09-04-vscode-theming-and-remote/` (a 24-exchange VS Code theming session). The first INDEX.md write failed with "modified since read"; on re-read, slot 04 was taken. I renamed this session's folder to `2026-05-09-05-skills-battery-and-conventions/` and merged both 2026-05-09-04 and 2026-05-09-05 entries into the index. Six 2026-05-09 sessions are now registered (01: GSD/VS Code setup; 02: this Claude Code's first session — CLAUDE.md + 7 agents; 03: parallel teacher-agent integration; 04: parallel VS Code theming pass; 05: this session — skills battery + conventions).
