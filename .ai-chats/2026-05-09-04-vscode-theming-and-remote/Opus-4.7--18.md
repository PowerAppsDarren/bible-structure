# Exchange 18: winget Microsoft.CascadiaCode not found

- **Timestamp:** 2026-05-09
- **Context:** User pasted a PowerShell session: `winget install Microsoft.CascadiaCode` returns "No package found matching input criteria."

## User Input

> PS C:\Users\DarrenNeese\src\bible-structure>  winget install Microsoft.CascadiaCode
> No package found matching input criteria.
> PS C:\Users\DarrenNeese\src\bible-structure>

## AI Response

Winget's package ID has changed over time. Try searching first:

```powershell
winget search cascadia
```

Likely IDs to try:
```powershell
winget install --id Microsoft.CascadiaCode -e
winget install --id Microsoft.CascadiaMono -e
```

**If winget keeps failing**, the most reliable path is the GitHub release direct download (PowerShell snippet provided to grab the latest ZIP and open the `ttf` folder in Explorer for "Install for all users"). After install, fully quit VS Code (not reload) and reopen — Apc should pick it up.

## Tool Calls

- (none — guidance only)

## Files Read/Modified

- (none)
