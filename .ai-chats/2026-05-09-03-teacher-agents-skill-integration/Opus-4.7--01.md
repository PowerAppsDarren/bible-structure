# Exchange 01: Integrate OneDrive bible-study bundle

- **Timestamp:** 2026-05-09
- **Context:** User had a bundle of six teacher-voice agents and a `deep-bible-study-devotional` skill in a OneDrive folder and wanted them dropped into the bible-structure repo and registered.

## User Input

> pls integrate all of these files into this repo: C:\Users\DarrenNeese\OneDrive - Super Power Labs\src\26-05-09--bible-study  ultrathink

## AI Response

(Summary of working response — full text was an exploratory walk-through ending with this completion report:)

> Integration done. Here's what landed:
>
> **`.claude/agents/`** — six new teacher-voice agents
> - `perry-stone.md`, `chuck-missler.md`, `john-barnett.md`, `jonathan-cahn.md`, `john-bevere.md`, `bill-creasy.md`
> - `TEACHERS.md` — overview + pairing suggestions (was the source `README.md`)
>
> **`.claude/skills/deep-bible-study-devotional/`** — extracted from the `.skill` bundle
> - `SKILL.md`, `references/` (4 files), `assets/example-isaiah-1.md`, plus `overview.html`
>
> **Docs updated**
> - `.claude/agents/README.md` — added a "Teacher-voice agents" table and a note that their devotional output usually belongs in `.personal/`, not the shared repo
> - `CLAUDE.md` — split the "Specialized agents" section into research agents vs. teacher-voice agents, with a pointer to the new skill
>
> **Things I deliberately did not do**
> - Did not stage or commit anything (per the repo's "no `git add -A`" rule and the user-confirmation default for risky actions). Run `git status` to review, then stage explicit paths.
> - Did not modify `.gitignore` — `.personal/` is still un-ignored, unchanged from before.
> - Renamed the bundled `README.md` to `TEACHERS.md` so it doesn't collide with the existing agents `README.md`. If you'd rather merge them or keep both, say the word.

## Tool Calls

- `Bash ls` on the OneDrive source folder → enumerated 9 items
- `Bash file` on `deep-bible-study-devotional.skill` → identified as Microsoft OOXML
- `Read` on `README.md` (source bundle)
- `Bash ls` on `.claude/agents/` and root → confirmed no `.claude/skills/` yet
- `Bash unzip` on the `.skill` file into `/tmp/skill-extract/`
- `Bash head` on `SKILL.md` and `perry-stone.md` to confirm structure
- `Read` on `.claude/agents/README.md`
- `Bash cp` (one chained command) — copied 6 teacher agents, renamed README → TEACHERS.md, made `.claude/skills/`, copied extracted skill tree, copied overview HTML
- `Edit` on `.claude/agents/README.md` (two edits — added Teacher-voice section + softened "all seven")
- `Edit` on `CLAUDE.md` — replaced "Specialized agents" section with two-tier listing

## Function Results

- Source folder: `bill-creasy.md`, `chuck-missler.md`, `deep-bible-study-devotional.skill`, `deep-bible-study-skill-overview.html`, `john-barnett.md`, `john-bevere.md`, `jonathan-cahn.md`, `perry-stone.md`, `README.md`
- Skill extracted to: `deep-bible-study-devotional/{SKILL.md, references/{pushback-patterns,output-template,eden-directives-framework,trusted-teachers}.md, assets/example-isaiah-1.md}`
- Final `.claude/agents/` listing showed 13 agent `.md` files plus `README.md` and new `TEACHERS.md`.

## Files Read/Modified

**Read:**
- `C:/Users/DarrenNeese/OneDrive - Super Power Labs/src/26-05-09--bible-study/README.md`
- `C:/Users/DarrenNeese/src/bible-structure/.claude/agents/README.md`
- `head` of `perry-stone.md` and `SKILL.md`

**Created:**
- `.claude/agents/perry-stone.md`
- `.claude/agents/chuck-missler.md`
- `.claude/agents/john-barnett.md`
- `.claude/agents/jonathan-cahn.md`
- `.claude/agents/john-bevere.md`
- `.claude/agents/bill-creasy.md`
- `.claude/agents/TEACHERS.md`
- `.claude/skills/deep-bible-study-devotional/` (full tree from the extracted bundle + `overview.html`)

**Modified:**
- `.claude/agents/README.md` — added Teacher-voice agents subsection + table; softened "all seven agents" → "all research agents"
- `CLAUDE.md` — replaced single agent list with two-tier list (research + teacher-voice) and pointer to the new skill
