# Exchange 04 — Full rename saga: bible-/teacher- adjustments + research aggressive shorten

- **Timestamp:** 2026-05-09
- **Context:** This is the rename saga that walked through three states for the teacher agents and one aggressive-shortening pass for the research agents. Three user prompts; one final PowerShell pass that resolved everything.

## User Input — First prompt (interrupt mid-Exchange 03)

```
i hate long file names. could we take out "bible-" for all file names -- i mean look at the name of this repo... this whole thing is about the bible
actually, take out the word `teacher-` too
...
ultrathink
```

## My intermediate response (captured here for completeness)

I distinguished strict vs. broad readings:
- Strict: only files literally containing `bible-` (the six teacher files) get the prefix removed; `biblical-theologian` etc. don't match the literal substring.
- Broad: extend the same de-redundancy logic to `biblical-` prefix (different stem but same redundancy in this repo).

I went strict first. PowerShell rename of the six teacher files (`bible-teacher-X.md` → `X.md`) plus replace_all of `bible-teacher-` → empty across nine files (six agents + agents/README + TEACHERS.md + CLAUDE.md). One prose false positive surfaced: `agents/README.md` line 46 had "the curator goes deeper" left orphaned by the rename — fixed to "the cross-references agent goes deeper" (provisionally; this changed again later).

I then asked, via `AskUserQuestion`, whether to extend the rule to `biblical-`/`biographical-` research agents. User selected **"Aggressive shorten"** — which would shorten `scripture-exegete → exegete`, `biblical-theologian → theologian`, etc., AND shorten `cross-reference-curator → cross-references`.

## User Input — Second prompt (interrupt before I could execute aggressive shorten)

```
oh... wait
```

I held without executing.

## User Input — Third prompt (clarification, two consecutive sub-messages)

```
we do need `teacher-` in there. i want all the teachers to be grouped together so that when I go into the agents folder, it isn't all a huge mess
```

```
but i like the other abbreviations
...
```

## Final reconciled state

- **Teacher agents:** keep a `teacher-` prefix for grouping (so they cluster on `te-` in directory listings) — but drop `bible-`. Final form: `teacher-perry-stone.md`, `teacher-chuck-missler.md`, etc.
- **Research agents:** the user liked the aggressive shortening. Final names: `exegete`, `theologian`, `linguist`, `historian`, `geographer`, `biographer`, `cross-references`.

## Tool Calls (manifest)

One PowerShell script that handled everything:

1. Defined 13 mappings (6 teacher renames + 7 research renames).
2. Renamed each file using `Move-Item`.
3. Iterated over `.claude/agents/*.md`, `.claude/skills/**/*.{md,html}`, and root `CLAUDE.md`; for each file, applied each mapping via `.Replace()` (case-sensitive, so prose mentions of "Perry Stone" with capital letters were unaffected).
4. Reported the 16 updated files plus the final agents folder listing.

After the script: a follow-up `Grep` for residual `bible-teacher` references found only the historical session log (`.ai-chats/2026-05-09-02-claude-md-and-agents/Opus-4.7--05.md`), which I left alone per the verbatim convention. A targeted `Edit` to `.claude/agents/README.md` line 46 fixed a prose oddity introduced by `cross-reference-curator → cross-references` (added the word "agent" so the sentence read grammatically).

## Files Read / Modified

| Action | Files |
|--------|-------|
| Renamed | 6 teacher files (`bible-teacher-X.md` → `teacher-X.md`); 7 research files (`scripture-exegete.md` → `exegete.md`, etc.) |
| Content updated | All 13 agent files (their own `name:` fields); `.claude/agents/README.md`; `.claude/agents/TEACHERS.md`; `CLAUDE.md` |
| Prose fix | `.claude/agents/README.md` line 46 ("the cross-references agent" added) |

## Outcome

Final agents folder (alphabetical — `te-` cluster groups the teachers cleanly):

```
README.md
TEACHERS.md
biographer.md
cross-references.md
exegete.md
geographer.md
historian.md
linguist.md
teacher-bill-creasy.md
teacher-chuck-missler.md
teacher-john-barnett.md
teacher-john-bevere.md
teacher-jonathan-cahn.md
teacher-perry-stone.md
theologian.md
```

I noted that `cross-references` reads slightly awkward in prose subject position — the user could rename later if desired, but they kept the choice.
