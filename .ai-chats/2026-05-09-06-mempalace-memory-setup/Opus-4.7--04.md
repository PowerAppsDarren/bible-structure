# Exchange 04: Stop hook failed → switched to absolute path

- **Timestamp:** 2026-05-09
- **Context:** Stop hook fired at end of previous turn and failed. User pasted the harness error.

## User Input

> ● Ran 1 stop hook (ctrl+o to expand)
>   ⎿  Stop hook error: Failed with non-blocking status code: /usr/bin/bash: line 1:
>   mempalace: command not found

## AI Response

Diagnosed instantly: Claude Code on Windows runs hooks under `/usr/bin/bash` (Git Bash). Earlier `which claude` from Bash showed Bash uses its own PATH (`/c/Users/DarrenNeese/bin:/mingw64/bin:/usr/local/bin:…`) and does NOT inherit the Windows user PATH where `mempalace.exe` lives (`%USERPROFILE%\.local\bin`).

Fix: rewrote `.claude/settings.json` to use absolute Bash-style path `/c/Users/DarrenNeese/.local/bin/mempalace.exe` for all three hooks. Also rewrote `.mcp.json` to use full Windows path `C:\\Users\\DarrenNeese\\.local\\bin\\mempalace-mcp.exe` (escaped backslashes in JSON) — same PATH-visibility risk applies to whatever spawns the MCP server.

Smoke-tested by piping a fake hook payload through Bash to the absolute path:
```
echo '{"session_id":"test","transcript_path":"none","cwd":"."}' \
  | /c/Users/DarrenNeese/.local/bin/mempalace.exe hook run --hook stop --harness claude-code
```
→ `{}` (success — hook ran, no instructions to inject). Reported to user that reload/restart should make the Stop hook succeed.

## Tool Calls

- `Write .claude/settings.json` — three hooks now use `/c/Users/DarrenNeese/.local/bin/mempalace.exe`
- `Write .mcp.json` — `command` now `C:\\Users\\DarrenNeese\\.local\\bin\\mempalace-mcp.exe`
- `Bash echo '{…}' | /c/…/mempalace.exe hook run --hook stop --harness claude-code` — returned `{}`

## Function Results

```
{}
```

## Files Read/Modified

- **Modified:** `.claude/settings.json` — bare `mempalace` → `/c/Users/DarrenNeese/.local/bin/mempalace.exe` in all three hooks
- **Modified:** `.mcp.json` — bare `mempalace-mcp` → `C:\\Users\\DarrenNeese\\.local\\bin\\mempalace-mcp.exe`
