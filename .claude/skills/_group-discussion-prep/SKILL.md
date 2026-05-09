---
name: _group-discussion-prep
description: Generate small-group or Sunday-school discussion materials for a Bible chapter or passage — discussion questions, ice-breakers, key verses for memorization, and a leader's outline. Use when the user is preparing to lead a small group, says "discussion questions for [chapter]", "small group on [book chapter]", "Sunday school lesson on X", "questions for our Bible study", "prepare a discussion on [passage]", or asks for materials structured for group conversation rather than personal study. Produces a leader's prep packet with opening question, observation/interpretation/application questions, and a wrap-up — saveable as personal notes for the leader, or to a shared `teaching/` folder if the church wants a shared library.
---

# Group Discussion Prep

Generate a leader's prep packet for a small-group, Sunday-school, or Bible-study discussion of a chapter or passage. Structured for conversation, not solo study.

## Triggers

- "Discussion questions for Genesis 1"
- "Small group on Romans 8"
- "Sunday school lesson on the parables of Matthew 13"
- "Prepare a discussion on [passage]"
- "Questions for our Bible study this week"

## Repo context

Read `CLAUDE.md` first. Output destinations:

- **Personal (default for the leader):** `.personal/<user-email>/teaching/<book>-<chapter>-discussion.md` — your private prep, may include guesses about how members will respond.
- **Shared (if the church wants a discussion library):** `teaching/discussions/<book>-<chapter>.md` — factual, neutral framing, no denominational corner-painting.

Most leader prep is personal. Only push to shared if the user explicitly wants a shared library.

## Workflow

1. **Confirm the passage** (chapter, half-chapter, multi-chapter unit). Confirm the audience (small group, Sunday school, men's/women's group, mixed) — affects question depth and tone.
2. **Delegate exegetical grounding to the `exegete` agent** so the questions land on real interpretive cruxes, not vague impressions.
3. **Use the `theologian` agent** when the chapter raises doctrinal stakes (Romans 9, Hebrews 6, etc.) — the leader needs to know where the disagreements are before walking into the room.
4. **Generate the packet** in the structure below.

## Output structure

```
# [Book Chapter] — Discussion Prep

**Audience:** [small group / Sunday school / etc.]
**Estimated time:** [60 / 90 minutes]
**Key passage focus:** [verses 1–17 / the whole chapter / etc.]

## Opening question (5 min)
[An ice-breaker tied to the chapter's theme, accessible without prior reading]

## Read together (10 min)
[Suggested verses to read aloud; who reads what; whether to use one translation or compare]

## Observation questions — what does the text say? (15 min)
- Q1
- Q2
- Q3

## Interpretation questions — what does it mean? (20 min)
- Q1 [with interpretive options the leader should be aware of]
- Q2
- Q3

## Application questions — what does it look like in our lives? (15 min)
- Q1
- Q2

## Memorize together
[1–2 verses suitable for memorization]

## Wrap-up (5 min)
[A closing prayer prompt or question that sends the group home thinking]

## Leader notes
- **Likely sticking points** — places the discussion may stall or get heated
- **Key cross-references** to have ready
- **Background** — historical / cultural context the leader should know but not necessarily teach
- **Common misreadings** — what the passage is *not* saying, in case it comes up
```

## Composition

- Orchestrates **exegete** (interpretive grounding) and **theologian** (doctrinal stakes).
- Pairs with **_deep-bible-study-devotional** if the leader wants the full chapter walk first, then the discussion packet.
- Pairs with **_chapter-readme-fill** if the shared chapter README's Questions section needs better questions — the discussion packet's Application questions can seed that.

## Avoid

- **Leading questions** that fish for a predetermined answer. Honest questions invite real engagement.
- **Yes/no questions** in the interpretation and application sections. They kill conversation.
- **Denominational corner-painting** — present the major positions where the chapter raises disputed doctrine, don't pre-decide for the group.
- **Too many questions.** A 60-minute discussion can sustain 6–10 substantial questions, not 30.
