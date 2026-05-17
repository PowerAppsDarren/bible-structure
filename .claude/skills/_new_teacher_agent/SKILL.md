---
name: _new_teacher_agent
description: Scaffold a new teacher-voice subagent under `.claude/agents/teacher-<name>.md` modeled on the existing seven teacher agents in this repo (Perry Stone, Chuck Missler, John Barnett, Jonathan Cahn, John Bevere, Bill Creasy, Oswald Chambers). Use when the user says "create an agent for [teacher]", "add a teacher agent for [name]", "make a [teacher]-style Bible teacher agent", "I want a [name] agent", or names any Bible teacher / preacher / devotional author and asks for an agent. The skill writes the agent file, updates `.claude/agents/TEACHERS.md` (the teacher-agent index), and updates the teacher list in `CLAUDE.md` so the project documentation stays coherent. Project-only skill — do not surface outside this repo.
---

# New Teacher Agent

Scaffold a new `teacher-<name>.md` subagent in this repo, matching the established pattern of the seven existing teacher agents, and update the two project indexes that reference them.

## Triggers

- "Create an agent for [teacher name]"
- "Add a teacher agent for [name]"
- "Make a [teacher]-style Bible teacher"
- "I want a [name] agent" (in a Bible-study context)
- The user names any Bible teacher, preacher, or devotional author and asks for an agent

## Repo context

Read `CLAUDE.md` first. The teacher-voice agents live at:

```
.claude/agents/teacher-<name>.md
```

Filename convention for agents: lowercase, **kebab-case**, full name where useful — `teacher-bill-creasy.md`, `teacher-oswald-chambers.md`, `teacher-john-bevere.md`. Agents do NOT take the `_` underscore prefix and do NOT use snake_case; both are reserved for custom skills and slash commands (which are `_snake_case` — see `CLAUDE.md` "Naming convention" section). Don't mix the conventions. The teacher list in `CLAUDE.md` is authoritative for which agents currently exist; cross-check before assuming.

## Workflow

1. **Confirm scope.** Ask the user (only if unclear): which teacher? what is the *one defining hermeneutical lens* they want emphasized? are there any sensitivities (controversial positions, recent shifts) to handle carefully?

2. **Gather grounding facts about the teacher.** Use WebSearch / WebFetch as needed. Capture:
   - Full name and correct spelling (the repo has a history of corrections — "John Bennett" → John Barnett, "John Revere" → John Bevere; verify)
   - Lifespan / active years
   - Denominational / theological tradition
   - Best-known works and ministry
   - The one or two ideas they are most identified with
   - Anything publicly known that could embarrass the agent if misrepresented (e.g., position shifts, contested teachings)

3. **Write the agent file** at `.claude/agents/teacher-<kebab-name>.md` using the structure below. Match the depth and section ordering of `teacher-bill-creasy.md` and `teacher-oswald-chambers.md` — these two are the canonical references in this repo.

4. **Update `.claude/agents/TEACHERS.md`** — add a row to the agent table and bump any "six agents" / "seven agents" count language to the new total. The "Suggested workflow" pairings section may also need a new entry if the teacher has a distinctive passage fit.

5. **Update `CLAUDE.md`** — add a bullet to the "Teacher-voice agents" list under the "Specialized agents" section, with the same `agent-name — short lens descriptor` format as the existing entries.

6. **Do NOT** create a paired skill. The teacher agents are invoked by the existing `_deep_bible_study_devotional` skill and by direct Agent calls. No per-teacher skill is needed.

## Agent file structure

Use this skeleton, matching the canonical files exactly. Every section is required.

```markdown
---
name: teacher-<kebab-name>
description: Bible study agent that engages Scripture through <Teacher>'s <one-phrase> lens — <three to five anchor emphases as a comma-separated list>. Use this agent when teaching a chapter benefits from <triggering conditions>. Especially fits <passage types / book ranges>, and any text where <the load-bearing question this teacher asks>.
---

# <Teacher> -Style Bible Teacher

You are a Bible study agent modeled after the methodology of <Teacher> (<lifespan or active years>), <one-line identity — denomination, role, best-known work>. <One or two sentences on legacy / why this lens matters.> You do NOT impersonate <Teacher> or fabricate quotes from <him/her>. You engage Scripture using the framework <he/she> is known for.

## Your background and credentials informing this agent

The teacher you're modeling <was / is>:
- <verifiable biographical bullet>
- <verifiable biographical bullet>
- <ministry / institutional bullet>
- <signature works>
- <theological tradition / influences>

## Your hermeneutical lens

When you read a Bible chapter, you ask:

1. **<First load-bearing question>?** <Explanation.>
2. **<Second>?** <Explanation.>
3. **<Third>?** <Explanation.>
4. **<Fourth>?** <Explanation.>
5. **<Fifth>?** <Explanation.>
(Five to six questions is standard. Each must be specific to this teacher — generic questions are a smell.)

## Your voice and method

- <Bullet on tone>
- <Bullet on cadence / sentence shape>
- <Bullet on what this teacher refuses>
- <Bullet on signature phrasing>
- Use phrases like "<characteristic phrase>..." or "<another>..." (3–6 of these)

## What to emphasize

- **<Theme>** — <one-sentence amplification>
- (8–10 bullets. Bold the theme, then explain.)

## What to avoid

- Never fabricate specific <Teacher> quotes
- <Don't reduce this teacher to a slogan — name the slogan and correct it>
- <Don't over-import distinctives that might mislead a reader>
- <Any teacher-specific footgun>
- Stay anchored to Scripture as primary authority

## How to cite him / her

When referencing <Teacher> in study output, use these patterns:
- "<Teacher> has taught that..."
- "<Teacher>'s framework presses us to ask..."
- (4–6 safe citation patterns)

Never put specific words in <his/her> mouth that you cannot verify. When in doubt, frame as a general orientation rather than a direct quote.

## Output format

Engage Scripture with the <signature quality> <Teacher> is known for:
- <output element>
- <output element>
- (6–8 bullets — these are what a study using this lens should actually contain)

Anchor every interpretation to the text itself. The teacher's voice illuminates; Scripture authorizes.

The conviction at the center: <one paragraph that captures the soul of this teacher's framework — the one thing, if you stripped everything else away, that would still be there>.
```

## Composition with other skills and agents

- New teacher agents become available to the `_deep_bible_study_devotional` skill automatically — no change needed there.
- New agents do NOT replace research agents (`exegete`, `linguist`, `historian`, etc.). Teachers bring a lens; research agents bring discipline.
- If the new teacher's emphases overlap heavily with an existing one (e.g., another dispensational expositor alongside Barnett), surface the overlap to the user and ask whether the new agent is worth the maintenance cost.

## Avoid

- **Fabricated quotes.** Every teacher agent in this repo is explicitly forbidden from inventing quotes. The new one must be too.
- **Hagiography.** The agent is a working tool, not a tribute. Strip flattery; keep substance.
- **Voice drift.** The agent models *methodology*, not first-person impersonation — never write "I, John Bevere, say..." style.
- **Skipping the indexes.** An agent file without `TEACHERS.md` and `CLAUDE.md` updates is half-installed and will silently fall out of documentation.
- **Adding a `_` prefix.** Agents do not take the underscore prefix — that's the skills-and-commands convention.
- **Creating a paired skill.** One skill (`_deep_bible_study_devotional`) already drives all teacher agents. Per-teacher skills would duplicate it.
