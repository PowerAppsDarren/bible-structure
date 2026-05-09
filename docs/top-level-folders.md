# Bible Study Vault: Top-Level Folder Structure

## TL;DR

For a serious Bible study Obsidian vault, I recommend **12 top-level folders** organized by content type. Your existing `books-of-bible` becomes your Scripture study home, `topics-of-study` handles thematic exploration, and the remaining folders capture the other major categories of biblical scholarship: word studies, people, places, timeline, theology, context, resources, teaching, personal reflection, and templates. A `_home` folder (underscore sorts it first) serves as your command center.

---

## Recommended Top-Level Structure

```
Bible Study/
│
├── _home/                    # Dashboard, reading plans, inbox
├── books-of-bible/           # YOUR EXISTING STRUCTURE (Scripture studies)
├── topics-of-study/          # YOUR PLANNED FOLDER (thematic studies)
├── word-studies/             # Hebrew & Greek analysis
├── people/                   # Biblical figures, scholars, theologians
├── places/                   # Geography, maps, archaeology sites
├── timeline/                 # Chronological studies, eras, events
├── theology/                 # Doctrine, systematic & biblical theology
├── context/                  # Historical, cultural, literary background
├── resources/                # Books, commentaries, tools, courses
├── teaching/                 # Sermons heard, lessons prepared
├── personal/                 # Journal, prayer, life application
└── templates/                # Reusable note templates
```

---

## Folder Breakdown with Rationale

### 1. `_home/` — Your Command Center
**Why underscore?** Sorts to the top of your folder list.

```
_home/
├── Dashboard.md              # Main MOC linking to all sections
├── Reading Plans/
│   ├── Current Plan.md
│   └── Archive/
├── Study Queue.md            # What's next on your plate
├── Inbox.md                  # Quick capture, unsorted notes
└── Weekly Review.md          # Reflection template
```

**Purpose**: Single entry point. When you open Obsidian, start here. Links out to everything else.

---

### 2. `books-of-bible/` — Scripture Studies (Your Existing Structure)
This is your canonical text study area. You already have this scaffolded with all 66 books.

**Suggested internal organization** (if not already):
```
books-of-bible/
├── _Scripture MOC.md
├── old-testament/
│   ├── 01-pentateuch/
│   │   ├── genesis/
│   │   │   ├── _Genesis Overview.md
│   │   │   ├── Genesis 01.md
│   │   │   ├── Genesis 02.md
│   │   │   └── ...
│   │   ├── exodus/
│   │   └── ...
│   ├── 02-historical/
│   ├── 03-wisdom/
│   ├── 04-major-prophets/
│   └── 05-minor-prophets/
└── new-testament/
    ├── 01-gospels/
    ├── 02-acts/
    ├── 03-pauline-epistles/
    ├── 04-general-epistles/
    └── 05-revelation/
```

**Key insight**: Each chapter file links OUT to word studies, people, places, topics. This folder stays focused on the text itself.

---

### 3. `topics-of-study/` — Thematic Exploration
This is where you trace themes, doctrines, and concepts ACROSS Scripture.

```
topics-of-study/
├── _Topics MOC.md
├── doctrines/                # Salvation, Trinity, Atonement, etc.
│   ├── Justification.md
│   ├── Sanctification.md
│   └── ...
├── themes/                   # Covenant, Kingdom, Redemption, etc.
│   ├── Covenant.md
│   ├── Kingdom of God.md
│   └── ...
├── ethics/                   # Moral questions, Christian living
│   ├── Marriage.md
│   ├── Work and Vocation.md
│   └── ...
├── commands/                 # One Anothers, Beatitudes, Ten Commandments
├── symbols/                  # Blood, Water, Light, Bread, etc.
├── types-and-shadows/        # OT types fulfilled in Christ
└── controversies/            # Baptism modes, election, spiritual gifts
```

**Why separate from theology?** Topics are thematic studies that trace a concept through Scripture. Theology is more systematic/organized doctrine. You'll link between them heavily.

---

### 4. `word-studies/` — Hebrew & Greek Analysis
The building blocks of understanding Scripture in its original languages.

```
word-studies/
├── _Word Studies MOC.md
├── hebrew/
│   ├── hesed.md              # Lovingkindness, covenant love
│   ├── shalom.md             # Peace, wholeness
│   ├── torah.md              # Law, instruction
│   └── ...
└── greek/
    ├── agape.md              # Love
    ├── logos.md              # Word
    ├── pistis.md             # Faith
    ├── charis.md             # Grace
    └── ...
```

**Power move**: Link every occurrence in your Scripture notes back to the word study. Over time, you'll see patterns emerge.

---

### 5. `people/` — Biblical Figures & Scholars
Everyone worth studying—from Adam to your favorite modern commentator.

```
people/
├── _People MOC.md
├── biblical-figures/
│   ├── old-testament/
│   │   ├── Abraham.md
│   │   ├── Moses.md
│   │   ├── David.md
│   │   └── ...
│   └── new-testament/
│       ├── Jesus Christ.md   # Could be its own massive section
│       ├── Paul.md
│       ├── Peter.md
│       └── ...
├── church-history/
│   ├── Augustine.md
│   ├── Luther.md
│   ├── Calvin.md
│   ├── Spurgeon.md
│   └── ...
└── modern-scholars/
    ├── N.T. Wright.md
    ├── D.A. Carson.md
    ├── John Piper.md
    └── ...
```

**Why track modern scholars?** When you read their works, you'll want to note their theological positions, strengths, and blind spots.

---

### 6. `places/` — Geography & Archaeology
The Bible is grounded in real places. Geography illuminates meaning.

```
places/
├── _Places MOC.md
├── cities/
│   ├── Jerusalem.md
│   ├── Babylon.md
│   ├── Rome.md
│   ├── Corinth.md
│   └── ...
├── regions/
│   ├── Galilee.md
│   ├── Judea.md
│   ├── Mesopotamia.md
│   ├── Asia Minor.md
│   └── ...
├── landmarks/
│   ├── Temple.md
│   ├── Tabernacle.md
│   ├── Mount Sinai.md
│   └── ...
└── maps/
    └── [Embedded images, Excalidraw files]
```

**Pro tip**: The Excalidraw plugin lets you create interactive maps that link to your place notes.

---

### 7. `timeline/` — Chronological Studies
Organizing events in time helps you see the sweep of redemptive history.

```
timeline/
├── _Timeline MOC.md
├── 01-creation-to-patriarchs/
├── 02-exodus-to-judges/
├── 03-united-kingdom/
├── 04-divided-kingdom/
├── 05-exile/
├── 06-return-and-restoration/
├── 07-intertestamental/       # CRITICAL - don't skip this
├── 08-life-of-christ/
├── 09-apostolic-age/
└── 10-church-history/
```

**Why intertestamental matters**: The 400 years between Malachi and Matthew explain Pharisees, Sadducees, synagogues, messianic expectations, Hellenization, and the Maccabean revolt. You can't fully understand the Gospels without it.

---

### 8. `theology/` — Systematic & Biblical Theology
Organized doctrinal study—how the church has understood Scripture.

```
theology/
├── _Theology MOC.md
├── biblical-theology/         # Tracing themes through Scripture progressively
│   ├── Kingdom Through the Ages.md
│   ├── Temple Theme.md
│   └── ...
├── systematic-theology/       # Organized by doctrinal category
│   ├── Theology Proper.md     # Doctrine of God
│   ├── Christology.md
│   ├── Pneumatology.md
│   ├── Anthropology.md
│   ├── Soteriology.md
│   ├── Ecclesiology.md
│   ├── Eschatology.md
│   └── ...
├── historical-theology/       # How doctrine developed
│   ├── Patristic Era.md
│   ├── Medieval Period.md
│   ├── Reformation.md
│   └── ...
└── creeds-and-confessions/
    ├── Apostles Creed.md
    ├── Nicene Creed.md
    ├── Westminster Confession.md
    └── ...
```

**Distinction from topics-of-study**: Topics trace themes through Scripture. Theology organizes what the church believes systematically.

---

### 9. `context/` — Background Studies
Understanding the world of the Bible.

```
context/
├── _Context MOC.md
├── historical/
│   ├── Ancient Near East.md
│   ├── Egyptian Empire.md
│   ├── Assyrian Empire.md
│   ├── Babylonian Empire.md
│   ├── Persian Empire.md
│   ├── Greek Empire.md
│   ├── Roman Empire.md
│   └── ...
├── cultural/
│   ├── Jewish Customs.md
│   ├── Greco-Roman World.md
│   ├── First Century Judaism.md
│   └── ...
├── literary/
│   ├── Hebrew Poetry.md
│   ├── Chiastic Structure.md
│   ├── Parallelism.md
│   ├── Genre Guide.md
│   └── ...
└── archaeological/
    ├── Dead Sea Scrolls.md
    ├── Tel Dan Inscription.md
    └── ...
```

**Why this matters**: The Bible wasn't written in a vacuum. Context prevents misinterpretation.

---

### 10. `resources/` — Your Library
Everything you're learning from—books, commentaries, courses, tools.

```
resources/
├── _Resources MOC.md
├── books/
│   ├── [Book Title] - [Author].md
│   └── ...
├── commentaries/
│   ├── genesis/
│   ├── romans/
│   └── ...
├── articles/
├── courses/
│   ├── [Course Name].md
│   └── ...
├── tools/
│   ├── Blue Letter Bible.md
│   ├── Logos Bible Software.md
│   └── ...
└── bibliographies/
    ├── Best Commentaries by Book.md
    ├── Theology Reading List.md
    └── ...
```

**Pro tip**: If you use Zotero for academic research, the Zotero integration plugin can sync your library.

---

### 11. `teaching/` — Learning & Preparing to Teach
Sermons you hear, lessons you prepare.

```
teaching/
├── _Teaching MOC.md
├── sermons-heard/
│   ├── [Date] - [Title] - [Speaker].md
│   └── ...
├── sermons-prepared/          # If you teach
│   └── ...
├── lessons/
│   ├── Sunday School/
│   ├── Small Group/
│   └── ...
├── courses-taken/
│   └── ...
└── podcasts/
    └── ...
```

---

### 12. `personal/` — Your Spiritual Life
The devotional, reflective, application side.

```
personal/
├── _Personal MOC.md
├── journal/
│   ├── 2025/
│   │   ├── 2025-01-31.md
│   │   └── ...
│   └── ...
├── prayer/
│   ├── Prayer Lists.md
│   ├── Answered Prayers.md
│   └── ...
├── testimonies/
├── life-application/
│   └── [How Scripture is changing my behavior]
└── memory-verses/
```

---

### 13. `templates/` — Reusable Note Templates
Consistency accelerates study.

```
templates/
├── Book Study Template.md
├── Chapter Study Template.md
├── Word Study Template.md
├── Person Study Template.md
├── Topic Study Template.md
├── Place Study Template.md
├── Sermon Notes Template.md
├── Book Notes Template.md
├── Daily Journal Template.md
└── Resource Template.md
```

---

## Visual Summary

| Folder | Purpose | Links TO | Links FROM |
|--------|---------|----------|------------|
| `_home` | Dashboard, navigation | Everything | Everything |
| `books-of-bible` | Scripture text study | Words, People, Places, Topics | Everything |
| `topics-of-study` | Thematic exploration | Scripture, Theology | Scripture, Theology |
| `word-studies` | Original language | Scripture passages | Scripture notes |
| `people` | Figures & scholars | Scripture, Timeline | Scripture, Resources |
| `places` | Geography | Scripture, Timeline | Scripture notes |
| `timeline` | Chronological | People, Places, Events | Scripture, Context |
| `theology` | Systematic doctrine | Scripture, Topics | Topics, Resources |
| `context` | Background studies | Scripture, Places | Scripture notes |
| `resources` | Library & tools | All content areas | Study notes |
| `teaching` | Learning & preparing | Scripture, Topics | Personal growth |
| `personal` | Devotional life | Scripture, Topics | Journal entries |
| `templates` | Note structures | N/A | All new notes |

---

## Optional Additional Folders

Depending on your study interests, you might add:

| Folder | When to Add |
|--------|-------------|
| `apologetics/` | If you study defense of the faith |
| `missions/` | If you're involved in missions or evangelism |
| `church/` | If you track local church matters, ministries |
| `languages/` | If you're learning Hebrew/Greek formally |
| `media/` | If you create or consume Bible-related media |
| `projects/` | For specific time-bound study projects |

---

## Implementation Recommendation

**Don't build it all at once.** Start with:

1. `_home/` with a basic Dashboard
2. `books-of-bible/` (you have this)
3. `templates/` with 2-3 essential templates
4. Pick ONE book to study deeply

As you study, you'll naturally create word studies, people notes, topic notes. Let the other folders emerge organically as needed. The structure exists to *serve* your study, not constrain it.

---

## File Naming Conventions

For consistency across your vault:

| Type | Convention | Example |
|------|------------|---------|
| Scripture | `[Book] [Chapter].md` | `Genesis 01.md` |
| People | `[Name].md` | `Abraham.md` |
| Places | `[Place Name].md` | `Jerusalem.md` |
| Words | `[transliteration].md` | `hesed.md` |
| Topics | `[Topic Name].md` | `Covenant.md` |
| Journal | `YYYY-MM-DD.md` | `2025-01-31.md` |
| Resources | `[Title] - [Author].md` | `Knowing God - J.I. Packer.md` |

---

*"All Scripture is breathed out by God and profitable for teaching, for reproof, for correction, and for training in righteousness."* — 2 Timothy 3:16
