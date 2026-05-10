# Exchange 02 — Teacher rename round 1 (filename ↔ frontmatter mismatch — wrong direction)

- **Timestamp:** 2026-05-09
- **Context:** I had flagged the teacher-voice agents' filename/`name` mismatch and offered to fix it. The simpler fix from the docs' point of view was to rename the *files* to match the long `name:` fields (`perry-stone.md` → `bible-teacher-perry-stone.md`). I went with that. **This turned out to be the wrong direction** — the user actually wanted shorter filenames — but I didn't know that yet.

## User Input

```
of course.
```

## Tool Calls (manifest)

- `PowerShell` Move-Item × 6: `bible-teacher-X.md` ← `X.md` for all six teacher names.
- `Glob .claude/agents/*.md` → verified renames.
- `Read .claude/agents/TEACHERS.md` (full) → noticed the table's "File" column still listed the old short filenames.

## My Visible Response (paraphrased — full text was a brief confirmation)

Renamed the six teacher files in one PowerShell pass and noted that `TEACHERS.md` still listed the old short filenames in its table — needed to be updated. Started reading TEACHERS.md to update.

## Files Read / Modified

| Path | Action |
|------|--------|
| `.claude/agents/perry-stone.md` → `bible-teacher-perry-stone.md` | Renamed |
| `.claude/agents/chuck-missler.md` → `bible-teacher-chuck-missler.md` | Renamed |
| `.claude/agents/john-barnett.md` → `bible-teacher-john-barnett.md` | Renamed |
| `.claude/agents/jonathan-cahn.md` → `bible-teacher-jonathan-cahn.md` | Renamed |
| `.claude/agents/john-bevere.md` → `bible-teacher-john-bevere.md` | Renamed |
| `.claude/agents/bill-creasy.md` → `bible-teacher-bill-creasy.md` | Renamed |
| `.claude/agents/TEACHERS.md` | Read |

## Outcome

This rename direction was undone in Exchange 04 after the user clarified they preferred short filenames.
