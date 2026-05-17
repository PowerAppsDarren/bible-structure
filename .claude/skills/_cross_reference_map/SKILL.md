---
name: _cross_reference_map
description: Build a structured cross-reference web for a passage — direct quotations, allusions, parallel passages, and typology — with citations, strength assessments, and source-language notes (LXX vs. MT). Use when the user asks "what passages connect to X", "trace this thread through Scripture", "where else is this quoted", "what's the OT background for [NT chapter]", "show me parallel passages to [verse]", "all uses of OT in Hebrews 1", or wants a deeper cross-reference set than what fits in a chapter README's small Cross References section. Distinct from _chapter_readme_fill, which produces 4–10 cross-refs inside a chapter README; this skill produces standalone cross-reference documents.
---

# Cross-Reference Map

Build a structured, deeper cross-reference web for a passage — beyond what fits in a chapter README's terse Cross References section.

## Triggers

- "Map all the cross-references for Romans 9"
- "What's the OT background for Hebrews 1?"
- "Where else is Genesis 15:6 quoted?"
- "All NT uses of Isaiah 53"
- "Parallel passages for [Synoptic pericope / Kings/Chronicles / Psalm doublet]"
- "Trace [theme] through Scripture" *(may also trigger _topic_trace)*

## Repo context

Read `CLAUDE.md` first. Output destinations:

- **Shared:** `commentary/<book>-<chapter>/cross-references.md` (or under `topics/<theme>/`) — factual, with sources cited.
- **Personal:** `.personal/<user-email>/cross-references/<passage>.md` — your private map, may include speculative connections you're still working through.

For chapter-level Cross References inside a chapter's own README (just 4–10 entries), use **_chapter_readme_fill** instead.

## Methodology

Delegate the harvesting to the **cross-references** agent. Distinguish four levels:

1. **Direct quotation.** NT explicitly cites OT ("it is written," "as it says," "the prophet says"). Note source language: did the NT author follow LXX, MT, or paraphrase? This often matters theologically (e.g., Hebrews quoting Psalm 8 from the LXX).
2. **Allusion.** NT echoes OT language without explicit quotation. Score by lexical overlap, structural parallel, and contextual fit. Beale & Carson, *Commentary on the NT Use of the OT*, is the standard reference; Hays, *Echoes of Scripture*, sets methodological bar.
3. **Parallel passage.** Two passages report or address the same material independently:
   - Synoptic Gospels (Matt / Mark / Luke).
   - Samuel-Kings ↔ Chronicles.
   - Psalm doublets (Ps 14 ↔ Ps 53; Ps 18 ↔ 2 Sam 22).
   - Prophetic doublets (Isa 2:2–4 ↔ Mic 4:1–3).
   - Decalogue (Ex 20 ↔ Dt 5).
4. **Typology.** Adam → Christ, Passover → Cross, Tabernacle → Christ/Church, Exodus → Salvation, David → Messiah. Only assert where the NT itself draws the line, or where the textual warrant is strong.

## Output structure

```
# Cross-references for [Book Chapter]

## Quotations
| NT verse | OT source | Textual form | Notes |
|---|---|---|---|
| Heb 1:5 | Ps 2:7 | LXX | "today I have begotten you" |

## Allusions
| Verse | Echo of | Strength | Notes |
|---|---|---|---|

## Parallels
| Passage A | Passage B | Type | Notes |
|---|---|---|---|

## Typology
[connections the NT itself draws, with chapter/verse anchors]

## Sources
[Treasury of Scripture Knowledge as baseline; NA28; Beale & Carson; Hays]
```

## Composition

- Orchestrates the **cross-references** agent.
- Feeds **_topic_trace** when the user wants a theme-level (not passage-level) web.
- Feeds **_chapter_readme_fill** with the top 4–10 connections to drop into a chapter README.

## Avoid

- Manufacturing connections from surface verbal coincidence — *does this passage actually illuminate that one?*
- Padding lists. Five excellent cross-refs > twenty mediocre.
- Asserting typology beyond textual warrant. Allegorical reading was historically common (Origen, Bernard) but isn't shared-repo content unless the NT itself draws the type-antitype line.
- Ignoring direction — "OT cited by NT" is the typical case, but "OT cites OT" (later prophets quoting earlier; Daniel citing Jeremiah) and "NT cites NT" (rare) also exist.
