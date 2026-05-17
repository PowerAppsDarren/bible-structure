---
name: _word_study
description: Produce a focused Hebrew, Aramaic, or Greek word study with academic discipline. Use ANY time the user asks about the original-language meaning of a word — "what does *hesed* mean", "study the Greek word for love in 1 Corinthians 13", "what's the Hebrew word behind 'wait' in Isaiah 40", "do a word study on agape / pistis / torah / shalom / kaphar", or names any Hebrew, Aramaic, or Greek term and asks for depth. Also triggers when a passage discussion surfaces "what's the original word for [English term] here". Produces a structured single-lemma study with lemma, transliteration, Strong's, semantic range, key occurrences, and theological significance — saveable to the shared `words/` folder or a personal notes folder.
---

# Word Study

Produce a single-lemma word study with academic rigor (BDB / HALOT for Hebrew & Aramaic, BDAG / Louw-Nida for Greek) and disciplined avoidance of common _word_study fallacies.

## Triggers

- "What does *hesed* / *agape* / *torah* / *pistis* mean?"
- "Study the [Hebrew | Greek | Aramaic] word for X"
- "Do a word study on Y"
- "What's the original-language word for [English term]?"
- "The Hebrew/Greek behind [verse]"

## Repo context

Read `CLAUDE.md` first. Word studies live in:

- **Shared:** `words/hebrew/<transliteration>.md` or `words/greek/<transliteration>.md` — factual, reference-quality, no denominational positioning, no extended copyrighted-lexicon quotes.
- **Personal:** `.personal/<user-email>/words/<transliteration>.md` — your private study notes that may include reflection or application.

Filename convention: lowercase transliteration, no diacritics — `hesed.md`, `agape.md`, `pistis.md`, `torah.md`. One file per lemma.

## Workflow

1. **Ask once if ambiguous:** which word? which language (when transliteration is shared, e.g., is "shalom" the noun or the verb root)? shared or personal destination?
2. **Delegate the academic content to the `linguist` agent.** That agent owns BDB / HALOT / BDAG methodology and the discipline against word-fallacies. The skill orchestrates; the agent produces.
3. **Wrap the agent's output** in the structure below.
4. **Save** to the chosen path. For personal output, use the user's email-named subfolder under `.personal/`.

## Output structure

```
# [transliteration] ([original script])

**Strong's:** H#### / G####
**Part of speech:** [verb stem / noun gender / particle / ...]
**Glosses:** [primary, secondary, theologically-loaded]

## Semantic range
[paragraph mapping how the word's range relates to typical English translation choices]

## Key occurrences
- **Genesis 1:1** — *bara*; this verb takes only God as subject throughout Gen 1.
- [4–8 representative passages, canonically ordered]

## Theological significance
[when load-bearing — *hesed* in covenant theology, *pistis Christou* debate, *almah* in Isa 7:14]

## Related words
[cognates, synonyms, antonyms within the language; LXX renderings where useful]

## Sources consulted
[BDB, HALOT, BDAG, Louw-Nida, NIDOTTE, NIDNTTE — short list]
```

## Composition with other skills and agents

- Orchestrates the **linguist** agent.
- Pairs with **_chapter_readme_fill** when the word anchors a chapter passage.
- Pairs with **_topic_trace** when one word carries a theme (e.g., *hesed* → covenant loyalty across the canon).
- Distinct from **_deep_bible_study_devotional**, which does its own embedded word work as part of a full chapter study.

## Avoid

- **Etymological fallacy.** Root meaning ≠ usage meaning. *Hyperetes* = "servant" in NT use, not "under-rower."
- **Illegitimate totality transfer.** Every meaning a word can have is not present in every occurrence.
- **Word-concept conflation.** A theological concept can be present without the specific word, and vice versa.
- **TDNT-style overload.** Older Kittel articles sometimes commit the very fallacies they should avoid.
- **Extended quotation** from copyrighted lexicons or modern translations.
