# Bible Structure — Study Template

A repo template with all books and chapters of the Protestant Holy Bible scaffolded out. It could be used for many reasons, but the simplest of reasons may be to serve as the beginning of a personal Bible study.

---

## Shared vs. Personal — How This Repo Works

This repo is designed for **group use**. It has two layers:

| Layer | Location | Pushed to Git? | Who edits it? |
|-------|----------|----------------|---------------|
| **Shared** | Everything *outside* `.personal/` | Yes | The group, via pull requests |
| **Personal** | `.personal/` | **No — never** | You, locally |

### Shared content (the repo itself)

The shared layer contains **reference material that is the same for everyone**: book overviews, people, places, timelines, cross-references, and curated chapter summaries. Once established, this content rarely changes (aside from the occasional correction). Everyone pulls from the same source of truth.

**Do not put personal study notes in the shared folders.** If you want to contribute a factual correction or add reference material that benefits everyone, open a pull request.

### Personal content (`.personal/`)

Your private study notes live in `.personal/` at the root of your local clone. This folder is **gitignored** — it will never be committed or pushed, so your notes stay on your machine.

The recommended structure mirrors the repo:

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

This makes it easy to find your notes — they sit in the same path as the shared content, just under `.personal/`. But this is a recommendation, not a requirement. Organize `.personal/` however works best for you.

**To get started:** create the `.personal/` folder in your local clone and start writing.

---

## What's Inside

- **66 books** organized in canonical order (`books-of-bible/`)
- **1,189 chapter folders**, each with its own `README.md` for shared reference notes
- **Book-level overviews** with author, date, and key themes for every book
- **Topics directory** (`topics-of-study/`) for cross-cutting themes and topical studies
- **Chapter template** ([README-TEMPLATE.md](README-TEMPLATE.md)) with sections for key verses, summary, notes, cross references, and questions

## Quick Start

1. Clone the repo (or your group's fork of it).
2. Create a `.personal/` folder in the root for your private notes.
3. Study. Use the shared content as reference. Write your personal notes in `.personal/`.
4. To improve the shared content, open a pull request.

## Documentation

| Document                                 | Description                                  |
|------------------------------------------|----------------------------------------------|
| [STRUCTURE.md](STRUCTURE.md)             | Full map of all 66 books and chapter counts  |
| [README-TEMPLATE.md](README-TEMPLATE.md) | Template for chapter-level study notes        |
| [CONTRIBUTING.md](CONTRIBUTING.md)       | How to use, fork, and contribute             |
| [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) | Community guidelines                         |
| [CHANGELOG.md](CHANGELOG.md)            | Version history                              |

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
