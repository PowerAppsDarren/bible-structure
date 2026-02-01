# Contributing

Thank you for your interest in this Bible study template. Whether you're using it for personal study or contributing improvements back to the project, this guide will help you get started.

---

## The Two-Layer Model

This repo separates **shared reference material** from **personal study notes**. Understanding this distinction is the most important thing before you start.

| What | Where | Shared? | Examples |
|------|-------|---------|----------|
| Reference material | `books-of-bible/`, `topics-of-study/`, root docs | **Yes** — pushed to git | Book overviews, people, places, timelines, cross-references |
| Personal notes | `.personal/` | **No** — gitignored, stays local | Your reflections, prayers, questions, sermon notes |

**Rule of thumb:** if it's a fact that's the same for everyone, it belongs in the shared repo. If it's *your* thought, reflection, or personal study note, it belongs in `.personal/`.

See the [README](README.md#shared-vs-personal--how-this-repo-works) for a fuller explanation.

---

## Getting Started

1. Clone the repo (or your group's fork of it).
2. Create a `.personal/` folder in the root of your local clone.
3. Start studying. Use the shared content as reference. Write your personal notes in `.personal/`.

That's it. The structure is already in place — just use it.

## Your Personal Notes (`.personal/`)

The `.personal/` folder is **gitignored** — nothing inside it will ever be committed or pushed. Your notes stay on your machine.

### Recommended structure

Mirror the repo layout so your notes are easy to find:

```
.personal/
├── books-of-bible/
│   ├── 01-Genesis/
│   │   ├── Genesis-01/
│   │   │   └── notes.md
│   │   └── Genesis-02/
│   │       └── notes.md
│   └── ...
└── topics-of-study/
    └── prayer/
        └── notes.md
```

This is a recommendation, not a requirement. Organize `.personal/` however works best for you — flat files, nested folders, or any other structure.

### Backing up your personal notes

Since `.personal/` is gitignored, **you are responsible for backing up your own notes.** Options include:

- A separate private git repo that tracks only `.personal/`
- Cloud sync (OneDrive, Dropbox, Google Drive, etc.)
- Manual backups to an external drive

---

## Shared Content — What Goes in the Repo

Everything outside `.personal/` is shared. This includes:

- **Book-level READMEs** (`books-of-bible/NN-BookName/README.md`) — overview, author, date, themes
- **Chapter-level READMEs** (`books-of-bible/NN-BookName/BookName-NN/README.md`) — shared summaries, key verses, cross-references
- **Topics of study** (`topics-of-study/`) — cross-cutting themes
- **Root documentation** — README, STRUCTURE, CONTRIBUTING, etc.

Shared content should be **factual, reference-quality, and beneficial to everyone**. Think of it as building a shared study Bible — the notes in the margins that any reader would find useful.

### What belongs in the shared repo

- Book and chapter summaries
- Key verses and cross-references
- People, places, and events (factual reference data)
- Timelines and historical context
- Topical studies grounded in Scripture

### What does NOT belong in the shared repo

- Personal reflections, prayers, or journal entries (put these in `.personal/`)
- Denominational or doctrinal commentary
- Content from copyrighted Bible translations
- Anything that is opinion rather than widely-accepted biblical scholarship

---

## Naming Conventions

### Book Folders

Each book folder is numbered and hyphenated:

```
NN-BookName
```

Examples: `01-Genesis`, `46-1-Corinthians`, `66-Revelation`

See [STRUCTURE.md](STRUCTURE.md) for the full list.

### Chapter Folders

Chapter folders use the book name followed by a zero-padded chapter number:

```
BookName-NN
```

Examples: `Genesis-01`, `Psalms-119`, `Revelation-22`

### File Names

Every folder contains a `README.md`. This is the only file required by the template. You are free to add additional files (images, PDFs, audio notes) alongside the README as needed.

## Chapter README Format

Each chapter `README.md` should follow the structure in [README-TEMPLATE.md](README-TEMPLATE.md):

- **Key Verses** — Notable verses from the chapter
- **Summary** — Brief overview of what happens
- **Notes** — Shared observations useful to everyone
- **Cross References** — Links to related passages
- **Questions** — Discussion questions for group study

Remember: personal reflections go in `.personal/`, not in the shared chapter READMEs.

## Book-Level README Format

Each book's `README.md` (e.g., `01-Genesis/README.md`) includes:

- Book name as heading
- Overview (brief description)
- Author, date written, chapter count
- Key themes

These are pre-filled in the template. Expand them with factual reference material via pull requests.

## Topics of Study

The `topics-of-study/` directory is for cross-cutting themes — topics that span multiple books and chapters. To add a topic:

1. Create a subfolder: `topics-of-study/prayer/`
2. Add a `README.md` with shared reference content.
3. Link back to relevant chapter folders in `books-of-bible/`.

For personal topical notes, use `.personal/topics-of-study/` instead.

---

## Contributing to the Shared Repo

If you'd like to improve the shared content, here's how:

1. Create a branch for your change.
2. Make your edits.
3. Open a pull request with a clear description of what you changed and why.

### What Makes a Good Contribution

- Adding factual reference content (people, places, historical context)
- Curating key verses and cross-references
- Fixing typos or factual errors in book metadata
- Improving the README-TEMPLATE.md structure
- Improving documentation (STRUCTURE.md, this file, etc.)

### What Doesn't Belong in a Pull Request

- Personal study notes (keep those in `.personal/`)
- Denominational or doctrinal commentary
- Content from copyrighted Bible translations

## Code of Conduct

Please read and follow the [Code of Conduct](CODE_OF_CONDUCT.md). The short version: be respectful, assume good faith, and keep things constructive.
