# Exchange 01: MemPalace request + scope/installer questions

- **Timestamp:** 2026-05-09
- **Context:** Fresh session at start of `bible-structure` repo. User opens with a GitHub link.

## User Input

> let's use this for easy memory retrieval: https://github.com/mempalace/mempalace

## AI Response

Loaded WebFetch via ToolSearch, then fetched the mempalace README. Reported back what mempalace is — a local-first CLI that mines `.claude/projects/` transcripts and project files into a semantic search store, with optional Claude Code hooks for auto-save. Noted it's complementary to the built-in auto-memory system documented in CLAUDE.md (auto-memory = curated facts; mempalace = full-fidelity transcript recall).

Asked two AskUserQuestion clarifications before installing anything:
1. **Scope** — install only / install+mine / full setup w/ hooks / just document.
2. **Installer** — uv / pip / let me detect.

## Tool Calls

- `ToolSearch select:WebFetch` — load WebFetch schema
- `WebFetch https://github.com/mempalace/mempalace` — read repo overview
- `AskUserQuestion` — scope + installer

## Function Results

WebFetch returned: mempalace is an open-source AI memory system, organizes memories as wings/rooms/drawers, local-first, recommended install via `uv tool install mempalace`, then `mempalace init <dir>`. Has Claude Code auto-save hooks for SessionStart/Stop/PreCompact-equivalent events. 96.6% retrieval recall on LongMemEval without LLM/API.

## Files Read/Modified

None.
