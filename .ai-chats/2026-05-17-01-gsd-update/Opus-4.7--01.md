# Exchange 01: update gsd

- **Timestamp:** 2026-05-17
- **Context:** Start of session. User wants to refresh the global GSD install.

## User Input

update gsd

## AI Response

(The assistant invoked the `gsd-update` skill, which routes to the
`get-shit-done/workflows/update.md` workflow. After detection and confirmation,
the assistant ran the npm installer and reported the result.)

### Detection / preview shown to user

> ## GSD Update Available
>
> **Installed:** 1.42.2
> **Latest:** 1.42.3
>
> ### What's New
>
> The CHANGELOG on GitHub's `main` branch hasn't been updated past `1.42.1` yet,
> so I can't show release notes for 1.42.2 → 1.42.3. Likely a patch release.
>
> ⚠️ The installer performs a clean install:
> - `~/.claude/commands/gsd/` wiped and replaced
> - `~/.claude/get-shit-done/` wiped and replaced
> - `~/.claude/agents/gsd-*` files replaced
>
> Your custom files (non-`gsd-` prefixed agents, custom commands, hooks,
> CLAUDE.md) are preserved.

### AskUserQuestion

- "Proceed with update from 1.42.2 → 1.42.3?" → **Yes, update now**

### Completion message

> ```
> ╔═══════════════════════════════════════════════════════════╗
> ║  GSD Updated: v1.42.2 → v1.42.3                           ║
> ╚═══════════════════════════════════════════════════════════╝
> ```
>
> ⚠️ **Restart Claude Code** to pick up the new commands.
>
> ⚠️ **Stale `gsd-sdk` on PATH** — installer flagged that
> `C:\Users\DarrenNeese\AppData\Roaming\npm\gsd-sdk.cmd` is still at 1.41.2.
> Fix with:
>
> ```
> npm install -g get-shit-done-cc@latest
> ```

## Tool Calls

- `Skill(gsd-update)` — entry point
- `Read` — `~/.claude/get-shit-done/workflows/update.md`
- `Bash` — `cat ~/.claude/get-shit-done/VERSION` → `1.42.2`
- `Bash` — `node check-latest-version.cjs --json` → `{"ok":true,"version":"1.42.3","reason":"ok"}`
- `Bash` — `curl ... CHANGELOG.md` (only showed entries up to 1.42.1)
- `AskUserQuestion` — confirm update
- `Bash` — `npx -y --package=get-shit-done-cc@latest -- get-shit-done-cc --claude --global`
- `Bash` — clear update caches

## Function Results

Key excerpts from the installer:

```
Get Shit Done v1.42.3
Installing for Claude Code to ~\.claude
✓ Installed 67 skills to skills/
✓ Installed get-shit-done
✓ Installed agents
✓ Wrote VERSION (1.42.3)
✓ Installed hooks (bundled)
✓ Wrote file manifest (gsd-file-manifest.json)
⚠ Skipping statusline (already configured)

⚠ gsd-sdk version mismatch — PATH resolves a stale SDK.
  Resolved gsd-sdk: C:\Users\DarrenNeese\AppData\Roaming\npm\gsd-sdk.cmd
  Resolved version: 1.41.2
  Installer version: 1.42.3
  Fix: npm install -g get-shit-done-cc@latest
```

## Files Read/Modified

- Read: `~/.claude/get-shit-done/workflows/update.md`, `~/.claude/get-shit-done/VERSION`
- Modified (outside repo): full reinstall under `~/.claude/get-shit-done/`,
  `~/.claude/agents/gsd-*`, `~/.claude/commands/gsd/`, `~/.claude/skills/gsd-*`,
  VERSION → `1.42.3`, `gsd-file-manifest.json` regenerated, update caches deleted.
- No files in the `bible-study` repo were changed.
