# Exchange 06 — 10-skill battery + multi-user `.personal/<email>/` paradigm

- **Timestamp:** 2026-05-09
- **Context:** The biggest single exchange in this session. The user asked for two things at once: a "full battery" of repo skills and a documentation/design recognition of the multi-user `.personal/<email>/` paradigm.

## User Input

```
create a full battery of repo skills that would work together as a system for bible study

also notice inside of .personal, each user would have their own folder, named as their email address. this template repo would be used within a church or a small group bible study. users of this repo would want to share their files, but this paradime will keep each users stuff separate. others in the bible study could look at other's notes or completly ignore them... their decision
```

## Reasoning Path

**Battery design.** I considered the four phases of small-group Bible study (study, group, personal, maintenance) and what natural workflows look like in each. Pruned ~15 candidate skills down to 10 that have clear, distinct triggers and don't overlap excessively. Each skill orchestrates the relevant agent(s) for academic content, then handles the user-facing format and output destination.

**Multi-user paradigm.** The user's framing reframed `.personal/` from "one user's gitignored private notes" (the old single-user model) to "shared-personal layer where each user has an email-named folder, committed to git, privacy by convention." This explained why the `#.personal/` line in `.gitignore` had been correctly commented out all along — the multi-user paradigm was the design intent, just under-documented. The two paradigms have different implications for skills (skills writing to `.personal/` should write to `.personal/<user-email>/`, not flat `.personal/`).

## Tool Calls (manifest)

12 parallel `Write` calls in one batch:

- `.claude/skills/_word-study/SKILL.md` (later prefixed; written as `word-study/` first)
- `.claude/skills/_cross-reference-map/SKILL.md`
- `.claude/skills/_character-study/SKILL.md`
- `.claude/skills/_place-study/SKILL.md`
- `.claude/skills/_topic-trace/SKILL.md`
- `.claude/skills/_group-discussion-prep/SKILL.md`
- `.claude/skills/_compare-notes/SKILL.md` (the multi-user feature — enumerates `.personal/*/`, preserves attribution)
- `.claude/skills/_personal-reflection/SKILL.md` (writes to `.personal/<user-email>/journal/`)
- `.claude/skills/_prayer-from-passage/SKILL.md` (also `.personal/<user-email>/`)
- `.claude/skills/_chapter-readme-fill/SKILL.md` (the only repo-maintenance skill — writes to shared `scripture/`)
- `.claude/skills/README.md` (battery overview, composition guide, two-layer discipline)
- `.personal/README.md` (rewrote to document multi-user paradigm, recommended subfolder layout, privacy conventions)

Plus three `Edit`s on existing files:

- `.gitignore` — replaced misleading `#.personal/` line with clear convention comment.
- `CLAUDE.md` — three edits: rewrote "Two-layer model" section for multi-user, added new "Skills" section, updated "Things to avoid".

(All `Edit` calls then got picked up — the file's full state at session end reflects all changes.)

## My Visible Response (excerpt — full response was substantial)

I delivered a table mapping the 10 skills to their phase and orchestrated agents:

| # | Skill | Phase | Orchestrates |
|---|---|---|---|
| 1 | `word-study` | Research | linguist |
| 2 | `cross-reference-map` | Research | cross-references |
| 3 | `character-study` | Research | biographer + historian |
| 4 | `place-study` | Research | geographer + historian |
| 5 | `topic-trace` | Research | theologian + cross-references |
| 6 | `group-discussion-prep` | Group | exegete + theologian |
| 7 | `compare-notes` | Group (multi-user) | none — reads `.personal/*/` |
| 8 | `personal-reflection` | Personal | (writes to `.personal/<email>/`) |
| 9 | `prayer-from-passage` | Personal | exegete |
| 10 | `chapter-readme-fill` | Maintenance | exegete + cross-references |

Plus the existing `deep-bible-study-devotional` (heavyweight all-in-one).

The multi-user paradigm propagated to: `CLAUDE.md` (rewritten two-layer section + new Skills section + Things to avoid), `.personal/README.md` (full multi-user docs), `.gitignore` (cleaned-up convention comment), and every personal-output skill (hardcoded `.personal/<user-email>/` as destination). The `compare-notes` skill is the multi-user feature.

I closed by flagging stale claims still pending review (root README, CONTRIBUTING, CHANGELOG 1.2.0 still describe `.personal/` as gitignored — old paradigm), and asking whether to scaffold `.claude/commands/` next.

## Files Read / Modified

| Action | Files |
|--------|-------|
| Created (skills) | 10 SKILL.md + skills/README.md |
| Created/rewrote | `.personal/README.md` |
| Edited | `.gitignore`; `CLAUDE.md` (3 edits) |
| Read for context | `.gitignore` (10 lines) before editing |
