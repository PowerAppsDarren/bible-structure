# Skills

This directory holds the project's skills. Claude Code loads them automatically and the model invokes them based on description-matching when the user's message fits.

For the user-invoked counterpart (typeable shortcuts), see `.claude/commands/` (when present).

## The battery

A coherent system for chapter-by-chapter, group-anchored Bible study. Skills compose with each other and with the agents in `.claude/agents/`.

### Heavyweight chapter walk

| Skill | Use when |
|---|---|
| `deep-bible-study-devotional` | The user wants a full, scholarly-yet-warm devotional walk through a chapter. All-in-one: word work, cross-refs, application, hook to next chapter. |

### Research skills (single-axis, narrower than the devotional)

| Skill | Use when | Orchestrates |
|---|---|---|
| `word-study` | A single Hebrew / Greek / Aramaic lemma deserves depth | `linguist` |
| `cross-reference-map` | A passage needs a deeper cross-ref web than what fits in a chapter README | `cross-references` |
| `character-study` | A biblical figure, church-history figure, or modern scholar | `biographer` (+ `historian`) |
| `place-study` | A city, region, landmark, or route | `geographer` (+ `historian`) |
| `topic-trace` | A theme traced redemptive-historically through the canon | `theologian` (+ `cross-references`, `linguist`) |

### Group skills

| Skill | Use when | Notes |
|---|---|---|
| `group-discussion-prep` | Preparing to lead a small group, Sunday school, or Bible study | Leader's prep packet — questions, opening, wrap-up |
| `compare-notes` | Surfacing what the group has been studying across `.personal/*/` folders | Multi-user, attribution-preserving |

### Personal skills (always write to `.personal/<user-email>/`)

| Skill | Use when |
|---|---|
| `personal-reflection` | Scaffolding a journal entry or chapter-anchored reflection |
| `prayer-from-passage` | Turning a passage into structured prayer (ACTS or passage-suggested form) |

### Maintenance skills (write to the shared layer)

| Skill | Use when |
|---|---|
| `chapter-readme-fill` | Converting a stub `# Read Me` chapter README into reference-quality shared content |

## How skills compose

A typical group-week workflow:

1. **Leader prep** — `deep-bible-study-devotional` for the chapter (overnight if it's a heavy passage), then `group-discussion-prep` for the meeting.
2. **Member personal study** — `personal-reflection` and `prayer-from-passage` for individual journals; ad-hoc `word-study`, `character-study`, or `place-study` when the chapter raises a specific question.
3. **Mid-week deepening** — `topic-trace` or `cross-reference-map` when the group's discussion surfaces a thread worth chasing.
4. **End of week** — `compare-notes` to see what the group has written across `.personal/*/`; insights from this often seed the next week's `chapter-readme-fill` work to make the shared layer richer.

## Two-layer discipline (mandatory across all skills)

- **Shared output** (`scripture/`, `topics/`, `words/`, `people/`, `places/`, etc.): factual, reference-quality, no denominational positioning, no copyrighted-translation extended quotes.
- **Personal output** (`.personal/<user-email>/`): first-person, devotional, application-focused — yours to keep, share, or delete.

Skills that produce shared output never write to `.personal/`. Skills that produce personal output never write outside the user's email folder. The skill descriptions above name the destination explicitly.

## Multi-user paradigm

`.personal/` is **intentionally tracked in git**, not gitignored. Each user has a folder named by their email address (e.g., `.personal/darren@neese.us/`, `.personal/sarah@church.org/`). Members share notes by pushing; privacy is by convention — if you don't want others to see something, don't commit it.

The `compare-notes` skill is the multi-user feature that surfaces what the group has been writing across all email folders.

## Adding a new skill

Each skill is a folder under `.claude/skills/<skill-name>/` with a `SKILL.md` file containing YAML frontmatter (`name`, `description`) plus the skill's instructions.

The `description` field is what Claude uses to decide when to invoke the skill, so write it with strong, specific triggers — concrete user phrases the skill should match. Vague descriptions don't fire reliably.

After adding or editing a skill, the next Claude Code session picks it up automatically.

## Skills vs commands

Skills are **model-invoked** — Claude decides when to use them based on description-matching. Commands (`.claude/commands/`) are **user-invoked** — the user types `/<name>` to trigger them deterministically. Both kinds of triggering matter, and the two coexist:

- Use a skill when "Claude should figure out the right time."
- Use a command when "I know exactly what I want, give me a typeable shortcut."

Many skills could have a corresponding command as a deterministic shortcut into the same workflow.
