# Exchange 02: Set CLAUDE_CODE_USE_POWERSHELL_TOOL=1 (global env var)

- **Timestamp:** 2026-05-17
- **Context:** Mid-sermon, user asked for a one-shot harness config change. Triggered `update-config` skill.

## User Input

> do this for me: Set CLAUDE_CODE_USE_POWERSHELL_TOOL=1

## AI Response

(Skill `update-config` invoked. Skill returned its instructions. Model asked AskUserQuestion to choose scope; user picked **Global**. Model then read `C:\Users\DarrenNeese\.claude\settings.json`, edited it to inject an `env` block, and confirmed.)

---

Added `env.CLAUDE_CODE_USE_POWERSHELL_TOOL=1` to `~/.claude/settings.json`. Restart Claude Code for it to take effect.

## Tool Calls

- `Skill(update-config, "Set environment variable CLAUDE_CODE_USE_POWERSHELL_TOOL=1")`
- `AskUserQuestion` — scope: Global / Project / Project-local. User chose **Global**.
- `Read("C:\\Users\\DarrenNeese\\.claude\\settings.json")`
- `Edit("C:\\Users\\DarrenNeese\\.claude\\settings.json", insert env block after autoUpdatesChannel)`

## Function Results

- Settings file read (105 lines): autoUpdatesChannel "latest", skipDangerousModePermissionPrompt true, theme "auto", effortLevel "medium", a large hooks block (SessionStart × 2, PostToolUse × 3, PreToolUse × 4), statusLine. No prior `env` block.
- Edit successful — `env: { "CLAUDE_CODE_USE_POWERSHELL_TOOL": "1" }` added immediately after `autoUpdatesChannel`.

## Files Read/Modified

- **Modified:** `C:\Users\DarrenNeese\.claude\settings.json` — added `env.CLAUDE_CODE_USE_POWERSHELL_TOOL = "1"` at user (global) scope. Requires Claude Code restart to take effect.
