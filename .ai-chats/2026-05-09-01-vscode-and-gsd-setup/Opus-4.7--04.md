# Exchange 04: Install GSD + Node.js

- **Timestamp:** 2026-05-09
- **Context:** User authorizes installation of all prerequisites and GSD itself, and asks that it be kept up to date.

## User Input

> yes get it installed and configured and keep it up to date

(Followed by, in a later turn after Node was discovered missing:)

> install all that's needed. go

## AI Response (summary of actions)

1. **Tried `npx get-shit-done-cc@latest --claude --global` via Bash** → exit 127, `npx: command not found`.
2. **Retried via PowerShell** → same: `npx` not recognized.
3. **Checked for Node.js**: `Get-Command node, npm, npx -ErrorAction SilentlyContinue` returned nothing — Node was not installed.
4. **Reported back** to user: Node.js missing; offered to install via `winget install OpenJS.NodeJS.LTS`.
5. After explicit "install all that's needed. go" approval:
   - Ran `winget install --id OpenJS.NodeJS.LTS --silent --accept-source-agreements --accept-package-agreements`. Successfully installed Node.js v24.15.0 (msstore source agreed; admin elevation requested by winget).
   - Refreshed the PowerShell session's `$env:Path` from machine + user environment, then verified: `node --version` → `v24.15.0`, `npm --version` → `11.12.1`.
   - Ran `npx -y get-shit-done-cc@latest --claude --global`. Output:
     - Installed 66 skills, agents, hooks, statusline, manifest.
     - **Warned**: `gsd-sdk` shim not on PATH because using `npx`; recommended `npm install -g get-shit-done-cc` for a persistent shim.
   - Followed up with `npm install -g get-shit-done-cc` → `added 99 packages in 18s`.
   - Verified: `Get-Command gsd-sdk` → `C:\Users\DarrenNeese\AppData\Roaming\npm\gsd-sdk.ps1`; `gsd-sdk --version` → `gsd-sdk v1.41.1`.

## Final state

- Node.js LTS 24.15.0 + npm 11.12.1 installed system-wide.
- GSD v1.41.1 installed globally:
  - 66 skills, agents, hooks under `~/.claude/`
  - `gsd-sdk` shim on PATH at `~/AppData/Roaming/npm/gsd-sdk.ps1`
- Update procedure: `npm install -g get-shit-done-cc@latest`.
- npm itself has a minor update available (`11.12.1 → 11.14.1`) — flagged but not applied.

## Tool Calls

- `Bash`: `npx -y get-shit-done-cc@latest --claude --global` (failed: no `npx`)
- `PowerShell`: same command (failed: no `npx`)
- `PowerShell`: `Get-Command node, npm, npx -ErrorAction SilentlyContinue` (empty)
- `PowerShell`: `winget install --id OpenJS.NodeJS.LTS --silent --accept-source-agreements --accept-package-agreements`
- `PowerShell`: PATH refresh + `node --version; npm --version`
- `PowerShell`: PATH refresh + `npx -y get-shit-done-cc@latest --claude --global`
- `PowerShell`: PATH refresh + `npm install -g get-shit-done-cc`
- `PowerShell`: PATH refresh + `Get-Command gsd-sdk`; `gsd-sdk --version`

## Function Results (key excerpts)

```
Successfully installed Node.js (LTS) v24.15.0
node v24.15.0
npm 11.12.1

GSD installer output:
✓ Installed 66 skills to skills/
✓ Installed get-shit-done
✓ Installed agents
✓ Wrote VERSION (1.41.1)
✓ Configured update check hook
✓ Configured context window monitor hook
✓ Configured prompt injection guard hook
✓ Configured read-before-edit guard hook
✓ Configured statusline
⚠ GSD SDK files are present but gsd-sdk is not on your PATH.

After npm install -g:
added 99 packages in 18s

gsd-sdk.ps1 → C:\Users\DarrenNeese\AppData\Roaming\npm\gsd-sdk.ps1
gsd-sdk v1.41.1
```
