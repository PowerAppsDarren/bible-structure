---
name: character-study
description: Produce a structured biographical study of a biblical figure (Abraham, David, Esther, Paul, Peter, Mary), a church history figure (Augustine, Luther, Calvin, Spurgeon), or a modern biblical scholar (N.T. Wright, D.A. Carson, Bauckham). Use when the user asks "study Abraham", "tell me about David's life", "give me a character study on Paul", "what was Augustine's contribution", "who was Caiaphas", "deep dive on Esther", or names any biblical, church-historical, or contemporary figure and asks about their life, contributions, or theological significance. Produces a chronologically-organized biography with theological significance, key passages, and cross-references — saveable to the shared `people/` folder or a personal notes folder.
---

# Character Study

Produce a biographical study with chronological structure, theological significance, and proper distinction between Scripture, scholarly inference, and tradition.

## Triggers

- "Study [biblical figure]" / "Character study on Abraham / David / Paul / Esther"
- "Tell me about [biblical or church-history figure]'s life"
- "Who was [name]?"
- "[Modern scholar]'s position on X" *(may also trigger topic-trace or theological lookup)*
- "Trace the life of [figure]"

## Repo context

Read `CLAUDE.md` first. Output destinations:

- **Shared:** `people/biblical-figures/<name>.md`, `people/church-history/<name>.md`, or `people/modern-scholars/<name>.md` — factual, no hagiography, no polemic against living scholars.
- **Personal:** `.personal/<user-email>/people/<name>.md` — your private notes that may include reflection or application.

Filename convention: full common name as written (`Abraham.md`, `Paul.md`, `Augustine of Hippo.md`, `John Calvin.md`, `N.T. Wright.md`). When the figure has multiple biblical names (Saul → Paul, Jacob → Israel), use the more common one and note alternates in the file.

## Workflow

1. **Identify category** — biblical figure (OT or NT), church history (patristic / medieval / Reformation / modern), or contemporary scholar. The methodology differs.
2. **Delegate to the `biographer` agent** for the structural content; pull in the **historian** agent when historical-cultural context is load-bearing (e.g., understanding Caiaphas requires Second Temple political context).
3. **Wrap output** in the structure below.
4. **Save** to the chosen path.

## Output structure

```
# [Name]

**Lived:** [dates or canonical period]
**Tradition / role:** [denomination, school, biblical role]
**Known for:** [one line]

## Biography
[chronological narrative or bulleted timeline]

## Theological / canonical significance
[paragraph — what this person contributes to the redemptive-historical narrative or to the church]

## Key works / key passages
[For biblical figures: chapter/verse anchors. For church history: major works with original-language titles where standard. For modern scholars: published works with brief contents.]

## Cross-references
[Links into scripture/, theology/, topics/]

## Sources
[ABD, ODCC, Pelikan, primary works — short list]
```

## Composition

- Orchestrates the **biographer** agent (and **historian** for context).
- Pairs with **topic-trace** when a biblical figure embodies a theme (Abraham ↔ faith and covenant; Moses ↔ deliverance and law; David ↔ messianic kingship).
- Pairs with **place-study** for figures defined by location (Jonah → Nineveh; Paul → Asia Minor / Mediterranean).
- Pairs with **cross-reference-map** for figures heavily echoed elsewhere (Adam in Romans 5 / 1 Cor 15; Melchizedek in Hebrews 7).

## Avoid

- **Hagiography.** Don't paint biblical figures as morally untroubled; they aren't.
- **Polemic against living scholars.** Note critiques only where widely recognized in the field.
- **Treating non-canonical legends as canonical.** Mention rabbinic, pseudepigraphal, or hagiographic traditions only as supplementary, marked clearly.
- **Sensational or apocryphal claims** (Paul's appearance, Mary Magdalene as a prostitute, etc., where Scripture doesn't say).
- **Pretending denominational neutrality means traditions don't exist.** Reformed vs. Wesleyan vs. Catholic readings of Augustine are real and worth naming.
