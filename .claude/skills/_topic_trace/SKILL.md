---
name: _topic_trace
description: Trace a biblical theme, doctrine, or concept across the canon — covenant, kingdom of God, prayer, fear of the Lord, atonement, election, the day of the Lord, faith, suffering. Use when the user asks "trace [theme] through Scripture", "do a topical study on prayer / covenant / kingdom / faith", "what does the Bible teach about X", "where does [theme] start and how does it develop", "all references to [doctrine]", or wants the redemptive-historical sweep of a single concept. Produces a thematic study with canonical trajectory (creation → fall → covenants → Christ → consummation), key passages anchored at each stage, and theological significance — saveable to the shared `topics/` folder or a personal notes folder.
---

# Topic Trace

Trace a biblical theme, doctrine, or concept redemptive-historically through the canon. Distinct from a single-passage exegesis (use **_deep_bible_study_devotional** or the `exegete` agent for that) and from a systematic-theology entry (use the `theologian` agent for that).

## Triggers

- "Trace [theme] through Scripture"
- "Topical study on prayer / covenant / kingdom / faith / atonement"
- "What does the Bible teach about X?"
- "Where does [theme] start, and how does it develop?"
- "All references to [doctrine]"

## Repo context

Read `CLAUDE.md` first. Output destinations:

- **Shared:** `topics/<theme-name>/README.md` — factual, no denominational positioning.
- **Personal:** `.personal/<user-email>/topics/<theme-name>.md` — private notes that may include speculative connections or application.

Filename convention: kebab-case for the folder, with `README.md` for the main entry — `topics/covenant/README.md`, `topics/fear-of-the-lord/README.md`.

## Workflow

1. **Define the theme tightly.** "Faith" is sprawling; "faith as covenant trust in the Pauline epistles" is workable. Sharpen with the user if the theme is too broad.
2. **Delegate to the `theologian` agent** for biblical-theology methodology (canonical trajectory, redemptive-historical reading).
3. **Pull in `cross-references`** for the citation/allusion web.
4. **Pull in `linguist`** when a single Hebrew or Greek term carries the theme (e.g., *hesed* for covenant loyalty, *pistis* for faith).
5. **Wrap output** in the structure below.

## Output structure

```
# [Theme Name]

## Definition
[one paragraph — tight, with operational scope]

## Canonical trajectory
### Creation
[anchor passages]
### Fall
[anchor passages]
### Covenants (Noahic, Abrahamic, Mosaic, Davidic, New)
[anchor passages, with how the theme develops in each]
### Exile and return
[anchor passages]
### Christ
[anchor passages — the typological resolution]
### Church
[anchor passages]
### Consummation
[anchor passages — eschatological telos]

## Theological significance
[where this theme matters doctrinally, with major-tradition disagreements named neutrally if any]

## Key Hebrew / Greek terms
[*hesed*, *agape*, *dikaiosyne* — when the theme is anchored in a specific lemma]

## Cross-references
[links into scripture/, theology/, related topics in topics/]

## Sources
[Beale, Goldsworthy, Vos for biblical theology; standard systematic theologies for doctrinal context]
```

## Composition

- Orchestrates **theologian** (primary), **cross-references**, and **linguist** (when applicable).
- Different from **_cross_reference_map** (passage-level) and from **_deep_bible_study_devotional** (chapter-level).
- Feeds back into chapter-level work — many of the cross-references in a chapter README's Cross References section are themes that ultimately deserve their own topic page.

## Avoid

- **Anachronism.** Don't read later doctrinal categories (Trinity, hypostatic union, *sola fide*) back into texts that don't yet have them. Show how categories were forged from texts.
- **Endorsing one tradition.** Where Reformed / Wesleyan / Lutheran / Anglican / Catholic / Orthodox readings differ, present each fairly.
- **Conflating biblical and systematic theology.** Biblical theology traces themes through canon; systematic theology organizes by category. Different methods.
- **Proof-texting.** Each cited passage should illuminate the theme, not be a hook to hang a conclusion on.
