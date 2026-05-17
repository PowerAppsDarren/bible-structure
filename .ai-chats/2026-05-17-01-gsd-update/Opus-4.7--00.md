# AI Chat Session: GSD Update 1.42.2 → 1.42.3

- **Date:** 2026-05-17
- **Model:** Claude Opus 4.7 (1M context)
- **Topic:** Run `/gsd-update` to bring the global GSD install current
- **Tool:** Claude Code
- **Project:** bible-study
- **Exchange Count:** 1

## 💡 Conversation Summary

User invoked `update gsd`. The `gsd-update` skill ran end-to-end: detected the
global install at `~/.claude/` (v1.42.2), confirmed npm latest (v1.42.3),
prompted for confirmation, ran `npx -y --package=get-shit-done-cc@latest -- get-shit-done-cc --claude --global`,
and cleared the update cache. The install printed a warning about a stale
`gsd-sdk` shim on PATH (1.41.2) that the user will resolve separately with
`npm install -g get-shit-done-cc@latest`.

GitHub CHANGELOG.md on `main` had not yet been updated past 1.42.1, so no
release notes were displayable — treated as a minor patch release.

## 🔧 Technical Details

- **Installer command:** `npx -y --package=get-shit-done-cc@latest -- get-shit-done-cc --claude --global`
- **Result:** 67 skills reinstalled, agents replaced, VERSION bumped to 1.42.3, file manifest regenerated, statusline skipped (already configured).
- **Caches cleared:** `~/.claude/cache/gsd-update-check.json`, `~/.cache/gsd/gsd-update-check.json`.
- **Files modified:** none in the project repo. Only `~/.claude/` global config.

## 📚 Lessons Learned

- The published GitHub CHANGELOG.md can lag the npm release — don't block on changelog availability when the version-check JSON confirms a newer release.
- A second global GSD copy under `%AppData%\Roaming\npm\gsd-sdk.cmd` (the SDK shim) can drift independently of the `~/.claude/get-shit-done/` install. The installer surfaces this; resolve with a separate `npm install -g`.

## ⏭️ Next Steps

- User: restart Claude Code to pick up the new commands.
- User: run `npm install -g get-shit-done-cc@latest` to refresh the stale `gsd-sdk` shim on PATH (was 1.41.2 → should be 1.42.3).
- If any local GSD files had been hand-edited, run `/gsd-update --reapply` to merge them back; this install did not flag any patches.

## 📁 Exchange Index

- [01 — update gsd](./Opus-4.7--01.md)
