# Agents

This directory holds the project's specialized subagents. Claude Code loads them automatically — invoke via the Agent tool with `subagent_type: <agent-name>`, or just describe a task that fits an agent's description and the main Claude can delegate.

## The team

| Agent | Use when |
|-------|----------|
| `scripture-exegete` | Filling in or improving a chapter README; close reading of a single passage |
| `biblical-theologian` | Doctrinal questions; topical / thematic studies in `topics/` or `theology/` |
| `hebrew-greek-linguist` | Building word-study notes in `words/`; questions hinging on a Hebrew or Greek word |
| `biblical-historian` | Historical, cultural, archaeological context |
| `biblical-geographer` | Notes for `places/`; geography or routes (Exodus, Paul's journeys) |
| `biographical-researcher` | Notes for `people/` — biblical figures, church history, modern scholars |
| `cross-reference-curator` | Cross-References sections; tracing citation / allusion threads |

Each agent reads `CLAUDE.md` at the repo root for project conventions before producing output.

## Shared discipline

All seven agents follow the same shared-repo rules:

- **Two-layer model.** Output is for the *shared* repo — factual and reference-quality. Personal reflection belongs in `.personal/`.
- **No copyrighted translations.** Use KJV / ASV / WEB or paraphrase. Cite chapter / verse, not extended text.
- **No denominational positioning.** Where traditions disagree, name them and present each fairly without endorsing.
- **Naming conventions.** Books `NN-BookName/`, chapters `BookName-NN/`, words lowercase transliteration, places / people human-readable names.

## How agents divide labor

- The **scripture-exegete** does single-passage close reading. The **biblical-theologian** does cross-passage synthesis. Use the exegete for "what does Genesis 3 say"; the theologian for "what does Scripture say about original sin."
- The **cross-reference-curator** does mechanical cross-ref work — citation, allusion, parallel, typology. The exegete cites a few important refs; the curator goes deeper.
- The **hebrew-greek-linguist** does single-lemma word studies. The theologian uses lemmas to anchor doctrines but doesn't write the word-study itself.
- The **biblical-historian** handles temporal / cultural background; the **biblical-geographer** handles spatial / locational background. They overlap on archaeology — historian for "what did this find prove"; geographer for "where is this site."
- The **biographical-researcher** owns persons (biblical, historical, modern). The historian owns events and cultures.

When more than one agent could fit, the main Claude should pick the *narrowest* one — depth over breadth.

## Editing or adding agents

Each agent is a markdown file with YAML frontmatter (`name`, `description`, optionally `tools`, `model`). The filename must match `name`. After editing, the next Claude Code session picks up the changes automatically.

To add an eighth agent, copy any existing file as a template and update `name`, `description`, and the system prompt. Keep the specialization distinct from the existing seven so the main Claude can pick the right one.

Candidates the planning doc (`____bible-study-top-level-folders.md`) suggests but the team currently lacks:

- A **timeline / chronology** specialist (overlaps with `biblical-historian`).
- A **commentary curator** that knows the landscape of major commentary series (NICOT / NICNT, BECNT, Word, Pillar, Hermeneia, Tyndale, ICC).
- A **homiletics / teaching** specialist for `teaching/` — but this is the kind of content that belongs more in `.personal/` than in the shared repo.
