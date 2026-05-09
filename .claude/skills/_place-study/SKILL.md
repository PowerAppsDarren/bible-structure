---
name: _place-study
description: Produce a structured geographical study of a biblical place — a city (Jerusalem, Babylon, Corinth), region (Galilee, Judea, Asia Minor), landmark (Temple, Tabernacle, Mount Sinai), or route (Exodus, Paul's missionary journeys, the via Maris). Use when the user asks "where is [place]", "study Jerusalem", "what was Caesarea Philippi", "trace the Exodus route", "geography of Paul's second journey", "study the Sea of Galilee", or names any biblical place / region / route. Produces a structured study with location, geography, biblical role, archaeology, and modern status — saveable to the shared `places/` folder or a personal notes folder.
---

# Place Study

Produce a geographical study with disciplined identification confidence, physical setting, biblical role, and extrabiblical attestation.

## Triggers

- "Where is [place]?" / "Study [place]"
- "Geography of [region or journey]"
- "What was the [Temple / Tabernacle / Mount Sinai] like?"
- "Trace the [Exodus / Paul's first missionary journey / Israel's wilderness wanderings]"
- "Modern location of [biblical site]"

## Repo context

Read `CLAUDE.md` first. Output destinations:

- **Shared:** `places/cities/<Place Name>.md`, `places/regions/<Region>.md`, `places/landmarks/<Landmark>.md`, or `places/routes/<Route>.md` — factual, with confidence levels for site IDs.
- **Personal:** `.personal/<user-email>/places/<Place Name>.md` — private notes that may include personal pilgrimage memories or speculation.

Filename convention: human-readable place name as written — `Jerusalem.md`, `Sea of Galilee.md`, `Mount Sinai.md`, `Paul's Second Missionary Journey.md`.

## Workflow

1. **Classify** — single place, region, landmark, or route? The output differs.
2. **Delegate to the `geographer` agent** for the spatial content; pull in **historian** when an empire's control or a specific period is load-bearing (e.g., Roman-era Jerusalem under Herod).
3. **Wrap output** in the appropriate structure below.
4. **Save** to the chosen path.

## Output structure (single place)

```
# [Place Name]

**Modern:** [current name, country]
**Coordinates:** [approx. lat / lon]
**ID confidence:** [secure / probable / contested / unknown]
**Alternate names:** [biblical and historical variants — Salem / Jebus / Jerusalem; Luz / Bethel]

## Geography
[terrain, water sources, elevation, climate, strategic significance]

## Biblical significance
[first canonical appearance, major events with chapter/verse anchors, last canonical appearance]

## History
[pre-biblical, biblical-era, post-biblical]

## Archaeology
[notable finds, strata where relevant]

## Cross-references
[links into scripture/, people/]
```

## Output structure (route)

```
# [Route Name]

## Waypoints
| # | Place | Reference | Notes |
|---|---|---|---|

## Estimated distances and travel time
[Ancient foot-travel: ~15–20 miles / 24–32 km per day on good roads, less in mountains]

## Terrain encountered
[paragraph]

## Disputed segments
[Where the route is contested — Exodus route, location of Mount Sinai/Horeb, Galatian addressees (north vs. south)]
```

## Composition

- Orchestrates the **geographer** agent (and **historian** for period-specific context).
- Pairs with **_character-study** for figures defined by location (Jonah → Nineveh; Jesus' Galilee ministry).
- Pairs with **_chapter-readme-fill** when geography illuminates a chapter passage.

## Avoid

- Stating contested identifications as certain (Mount Sinai's location, Sodom and Gomorrah's site, the Exodus route, the location of Bethsaida or Cana — all genuinely disputed).
- Modern political projection onto biblical territory ("Israel" in Scripture covers different territory at different times and is not interchangeable with the modern state).
- Picture-postcard prose. Focus on what made a place strategically, economically, or theologically significant.
- Romanticized "the land where Jesus walked" tone — this is reference content.
