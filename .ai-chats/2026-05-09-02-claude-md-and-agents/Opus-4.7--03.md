# Exchange 03 — 7-agent research team creation (ultrathink)

- **Timestamp:** 2026-05-09
- **Context:** User asked for a reusable team of 7 research / theology agents stored in the repo. The system flagged the message with the `ultrathink` keyword for deeper reasoning.

## User Input

```
<system-reminder>
The user included the keyword "ultrathink", requesting deeper reasoning on this turn. Reason as thoroughly as the task warrants.
</system-reminder>

create a team of research and theology agents for me. let's reuse these agents. give me 7 agents. store these agents we can call on inside this repo! ultrathink
```

## Reasoning Path

Designed seven agents along the principal axes of biblical scholarship to ensure no two agents own the same lane:

- **Passage scope:** single passage (`scripture-exegete`) vs. canonical theme (`biblical-theologian`).
- **Language:** English exposition vs. original-language word study (`hebrew-greek-linguist`).
- **Domain:** textual (exegete, theologian, linguist), historical (`biblical-historian`), geographical (`biblical-geographer`), biographical (`biographical-researcher`).
- **Method:** exposition vs. mechanical cross-ref harvest (`cross-reference-curator`).

Considered but rejected for the initial seven:

- A homiletics / teaching specialist — `CONTRIBUTING.md` excludes sermon-style content from the shared layer; this kind of work belongs in `.personal/`, not the shared repo.
- A commentary-series curator (NICOT/NICNT/BECNT/Word/Pillar/Hermeneia) — overlaps with `biographical-researcher` (modern scholars) and `biblical-theologian`.
- A timeline / chronology specialist — overlaps with `biblical-historian`.

Both rejected candidates noted in `.claude/agents/README.md` as future possibilities.

## Tool Calls (manifest)

Eight parallel `Write` calls under `.claude/agents/`:

| Path | Purpose |
|------|---------|
| `.claude/agents/scripture-exegete.md` | single-passage close reading |
| `.claude/agents/biblical-theologian.md` | systematic + biblical theology synthesis |
| `.claude/agents/hebrew-greek-linguist.md` | original-language word studies |
| `.claude/agents/biblical-historian.md` | ANE / Second Temple / Greco-Roman context |
| `.claude/agents/biblical-geographer.md` | places, regions, routes |
| `.claude/agents/biographical-researcher.md` | biblical figures, church history, modern scholars |
| `.claude/agents/cross-reference-curator.md` | citations, allusions, parallels, typology |
| `.claude/agents/README.md` | team overview, division of labor, shared discipline |

Followed by one `Edit CLAUDE.md` to add a "Specialized agents" section before the AI-Chats section.

Each agent file has YAML frontmatter (`name`, `description`, `tools: Read, Grep, Glob, Edit, Write, WebSearch, WebFetch`) plus a system prompt covering: repo context (read CLAUDE.md first), methodology, sources, output format, things to avoid. The agent file contents are the authoritative verbatim record at the paths above.

## My Visible Response (verbatim)

> I'll create a team of 7 specialized subagents stored in `.claude/agents/` so Claude Code picks them up automatically across sessions. Each maps to one of the repo's content domains and is built to produce shared-layer reference content (factual, no denominational positioning, no copyrighted translation quotes).
>
> The team:
>
> | Agent | Domain | Folder home |
> |-------|--------|-------------|
> | `scripture-exegete` | Close reading of passages, chapter READMEs | `scripture/` |
> | `biblical-theologian` | Systematic + biblical theology, creeds | `theology/`, `topics/` |
> | `hebrew-greek-linguist` | Original-language word studies | `words/` |
> | `biblical-historian` | ANE / Second Temple / Greco-Roman context | (planned `context/`, `timeline/`) |
> | `biblical-geographer` | Cities, regions, routes | `places/` |
> | `biographical-researcher` | Biblical figures, church history, scholars | `people/` |
> | `cross-reference-curator` | Citations, allusions, parallels, typology | cross-cutting |
>
> Writing all eight files (7 agents + a team README) in parallel.

After writes succeeded:

> Now adding a brief Agents section to the root `CLAUDE.md` so future Claude sessions know the team exists.

After the edit:

> Done. The team is committed at `.claude/agents/`:
>
> ```
> .claude/agents/
> ├── README.md                       # team overview + division of labor
> ├── scripture-exegete.md            # single-passage close reading
> ├── biblical-theologian.md          # doctrinal + thematic synthesis
> ├── hebrew-greek-linguist.md        # original-language word studies
> ├── biblical-historian.md           # ANE / Second Temple / Greco-Roman context
> ├── biblical-geographer.md          # places, regions, routes
> ├── biographical-researcher.md      # figures, church history, scholars
> └── cross-reference-curator.md      # citations, allusions, parallels, typology
> ```
>
> A few design choices worth knowing:
>
> - **Each agent reads `CLAUDE.md` first.** That keeps repo-wide conventions (two-layer model, naming, copyright caution) in one place and propagates updates automatically — no need to edit seven prompts when a convention changes.
> - **Tools granted:** `Read, Grep, Glob, Edit, Write, WebSearch, WebFetch`. No Bash (these are content agents, not shell agents). No Agent (subagents shouldn't recursively spawn more subagents).
> - **Model:** unset, so they inherit from your session. If you want a specific tier per agent (e.g., Sonnet for research, Opus for synthesis), add `model: sonnet` etc. to the frontmatter.
> - **Division of labor in the README** explains where agents overlap and how the main Claude should pick — e.g., exegete = single passage, theologian = cross-passage synthesis; historian = events / culture, geographer = places, biographer = persons.
> - **What's deliberately missing:** a homiletics / teaching agent (that content arguably belongs in `.personal/`, not the shared repo) and a commentary-series curator (overlaps too much with theologian + biographer). Both noted as future candidates in the agents README.
>
> Updated the root `CLAUDE.md` with a pointer to the team. Future sessions will see them automatically.

## Files Read / Modified

| Path | Action | Approx. size |
|------|--------|--------------|
| `.claude/agents/scripture-exegete.md` | created | ~60 lines |
| `.claude/agents/biblical-theologian.md` | created | ~85 lines |
| `.claude/agents/hebrew-greek-linguist.md` | created | ~85 lines |
| `.claude/agents/biblical-historian.md` | created | ~95 lines |
| `.claude/agents/biblical-geographer.md` | created | ~95 lines |
| `.claude/agents/biographical-researcher.md` | created | ~95 lines |
| `.claude/agents/cross-reference-curator.md` | created | ~95 lines |
| `.claude/agents/README.md` | created | ~50 lines |
| `CLAUDE.md` | edited (added "Specialized agents" section before "AI-Chats protocol") | +14 lines |
