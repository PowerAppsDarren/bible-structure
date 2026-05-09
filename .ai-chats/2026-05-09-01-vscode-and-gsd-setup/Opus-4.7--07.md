# Exchange 07: Verify protocol compliance, build `/_wrapup` skill, register Windows scheduled task

- **Timestamp:** 2026-05-09
- **Context:** User asks two things in one turn — whether I followed the AI-Chats protocol for this session, and to encode that protocol as a `/_wrapup` skill. Mid-execution, user adds: "but to answer your question about chron job, yes" — confirming the local Task Scheduler approach from Exchange 06.

## User Input (turn 1)

> did you follow this protocol for this chat? c:\Users\DarrenNeese\src\bible-structure\.ai-chats\README.md
>
> add in this protocol to a skill called `/_wrapup`

## User Input (mid-tool injection)

> but to answer your question about chron job, yes.

## AI Response

**Compliance check:** Reported back honestly — first 5 exchanges were logged in `2026-05-09-01-vscode-and-gsd-setup/Opus-4.7--00..05.md` with `INDEX.md` updated, but Exchange 06 (and this Exchange 07) had not yet been written. The protocol expects either continuous updates or a wrap-up; we were due for a wrap-up.

**Skill creation:** Listed `~/.claude/skills/` to confirm the user-global skills directory exists (it does — populated heavily by GSD). Wrote `~/.claude/skills/_wrapup/SKILL.md` with frontmatter (`name`, `description`) and a step-by-step body distilling the v3.2 protocol:

1. Discover (`.ai-chats/`, today's folders, `INDEX.md`).
2. Pick or create the session folder (`YYYY-MM-DD-NN-kebab-description/`).
3. Determine the model filename prefix (`Opus-4.7`, `Sonnet-4.6`, etc.).
4. Write `--00.md` (summary template) and `--NN.md` (verbatim exchange template).
5. Update `INDEX.md` (Last Updated, totals, all three views, file listing).
6. Confirm to user; do not auto-commit.

Also included repo-specific reminders: never `git add -A`, treat `.personal/` as private, defer to `.ai-chats/README.md` on conflict.

**Scheduled task setup** (after the cron-yes confirmation):

- First attempt with `Register-ScheduledTask -LogonType S4U` failed: `Access is denied.` (S4U requires admin).
- Second attempt with `schtasks.exe` failed because of nested-quoting: a trailing `\"` got consumed and the log path became invalid.
- Solved by writing a wrapper script `C:\Users\DarrenNeese\bin\gsd-update.ps1`:
  ```powershell
  $log = Join-Path $env:LOCALAPPDATA 'gsd-update.log'
  "=== $(Get-Date -Format o) — running gsd update ===" | Out-File -FilePath $log -Append -Encoding utf8
  & npm install -g get-shit-done-cc@latest *>&1 | Out-File -FilePath $log -Append -Encoding utf8
  "=== exit $LASTEXITCODE ===`n" | Out-File -FilePath $log -Append -Encoding utf8
  ```
- Registered task: `schtasks /Create /SC WEEKLY /D MON /ST 09:00 /TN "GSD Weekly Update" /TR "powershell.exe -NoProfile -ExecutionPolicy Bypass -File C:\Users\DarrenNeese\bin\gsd-update.ps1" /F` → SUCCESS.
- Verified via `schtasks /Query`: Status=Ready, Next Run=2026-05-11 09:00:00, Run As=DarrenNeese, Schedule Type=Weekly.

## Tool Calls

- `Bash` → `ls C:\Users\DarrenNeese\.claude\skills` (confirms skills dir; lists 30+ existing skills, mostly GSD's)
- `Write` → `C:\Users\DarrenNeese\.claude\skills\_wrapup\SKILL.md`
- `Write` → `C:\Users\DarrenNeese\bin\gsd-update.ps1`
- `PowerShell` → `Register-ScheduledTask` (failed: Access denied)
- `PowerShell` → `schtasks /Create ...` with inline `-Command` (failed: quoting)
- `PowerShell` → `schtasks /Create ...` pointing at the wrapper (success)
- `PowerShell` → `schtasks /Query /TN "GSD Weekly Update" /V /FO LIST` (verified)

## Function Results (key)

```
SUCCESS: The scheduled task "GSD Weekly Update" has successfully been created.

TaskName: \GSD Weekly Update
Next Run Time: 5/11/2026 9:00:00 AM
Status: Ready
Task To Run: powershell.exe -NoProfile -ExecutionPolicy Bypass -File C:\Users\DarrenNeese\bin\gsd-update.ps1
Run As User: DarrenNeese
Schedule Type: Weekly
```

## Files Created/Modified

- `C:\Users\DarrenNeese\.claude\skills\_wrapup\SKILL.md` — new user-global skill encoding the AI-Chats v3.2 protocol.
- `C:\Users\DarrenNeese\bin\gsd-update.ps1` — wrapper script for the scheduled task.
- Windows Scheduled Task `GSD Weekly Update` — runs Mondays 09:00 local time as `DarrenNeese`.

## Lessons

- For Windows scheduled tasks running as the current logged-in user, `schtasks.exe` is friendlier than `Register-ScheduledTask` (no S4U/admin needed).
- When passing PowerShell commands through `schtasks /TR`, prefer pointing at a `.ps1` file; inline `-Command` strings get mangled by the shell's nested quoting.
