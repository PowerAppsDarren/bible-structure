---
name: _prayer_from_passage
description: Turn a Bible passage, chapter, or theme into structured prayer — adoration, confession, thanksgiving, supplication — anchored to the text rather than free-floating. Use when the user says "pray through [chapter]", "prayer based on [passage]", "help me pray Psalm 51", "turn this chapter into a prayer", "give me a prayer from today's reading", or wants to use Scripture as a template for prayer. Output is personal devotional — saves to the user's `.personal/<email>/` folder, not the shared layer.
---

# Prayer From Passage

Convert a passage, chapter, or theme into a structured prayer that's anchored in the text — using its language, imagery, and concerns — rather than improvising loose-strung phrases.

## Triggers

- "Pray through Psalm 51"
- "Turn [chapter] into a prayer"
- "Help me pray [passage]"
- "Prayer based on today's reading"
- "Pray the Lord's Prayer line by line"

## Repo context

Read `CLAUDE.md` first. Output destinations (always personal):

- `.personal/<user-email>/prayer/<passage>.md` — passage-anchored prayer.
- `.personal/<user-email>/prayer/lists/<topic>.md` — running prayer list seeded from a passage.
- `.personal/<user-email>/journal/YYYY-MM-DD.md` — if the prayer is part of a dated journal entry.

## Workflow

1. **Identify the passage** (or chapter, or theme).
2. **Lightly delegate to the `exegete` agent** to make sure the prayer is rooted in what the text actually says — not a free-association of words that happen to appear.
3. **Frame as ACTS** (Adoration / Confession / Thanksgiving / Supplication), or another structure if the passage suggests one (e.g., the Lord's Prayer's six petitions; lament structure for Psalms of lament; covenant structure for Deuteronomy).
4. **Use the passage's own language** wherever possible (KJV, ASV, WEB, or paraphrase).
5. **Save** to the user's email folder.

## Output structure (default ACTS form)

```
# Prayer from [Book Chapter]

**Prayed on:** YYYY-MM-DD
**Passage:** [Book Chapter:Verses]

## Adoration
[Praise drawn from how the passage describes God — His character, acts, attributes, names. Use the passage's own language.]

## Confession
[Confess where the passage exposes us — sins named in the text, idols revealed, lies believed, complacencies surfaced.]

## Thanksgiving
[Thank for what the passage shows God has done — historically, in Christ, in the user's own life.]

## Supplication
[Ask in line with what the passage invites — for the user, for the group, for the church, for the world. Specific, not generic.]

## A line to carry today
[One short sentence drawn from the passage to repeat through the day.]
```

## Alternative structures

- **Lament Psalm pattern:** invocation → complaint → trust → petition → vow of praise.
- **The Lord's Prayer:** Father / hallowed name / kingdom come / will done / daily bread / forgiveness / lead us not / deliver us.
- **Covenant pattern (Deuteronomy):** preamble → historical prologue → stipulations → blessings/curses → response.

When the passage's own structure suggests a form, prefer it over generic ACTS.

## Composition

- Lightly orchestrates the **exegete** agent for textual grounding.
- Pairs with **_personal_reflection** when the user wants both reflection and prayer in one journal entry.
- Pairs with **_deep_bible_study_devotional** when the user wants the prayer as the closing section of a fuller chapter walk.

## Avoid

- **Free-floating prayer that ignores the text.** The point of this skill is to be passage-anchored. If the prayer could be prayed without the passage, it isn't really *from* the passage.
- **Sermonic flourishes.** Prayer is not a lecture. Keep it direct.
- **Performance language.** Honest beats ornate.
- **Making the prayer about the passage rather than to God.** Stay in second-person address ("You"), not third-person commentary about God.
- **Saving to the shared layer.** Prayer is personal output — `.personal/<user-email>/` always.
