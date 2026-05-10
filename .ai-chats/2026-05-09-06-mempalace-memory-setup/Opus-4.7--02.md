# Exchange 02: uv not installed → chose winget

- **Timestamp:** 2026-05-09
- **Context:** User answered: scope = "Full setup w/ auto-save hooks", installer = "Use uv". CLAUDE.md was concurrently updated by the user to add a third bullet about the multi-user `.personal/<email>/` paradigm — informational only, no action required.

## User Input

User's AskUserQuestion answers:
> "How far do you want me to take this right now?" = **Full setup w/ auto-save hooks**
> "Do you have `uv` installed, or should I use pip?" = **Use uv**

## AI Response

Probed for uv and python via PowerShell — neither was on PATH. Reported the blocker and asked one more question via AskUserQuestion: how to obtain uv?
- `winget install astral-sh.uv` (recommended on Windows)
- Official PowerShell installer (`irm https://astral.sh/uv/install.ps1 | iex`)
- "I'll install it myself"

## Tool Calls

- `PowerShell uv --version; python --version` — both not found

## Function Results

```
uv: The term 'uv' is not recognized as a name of a cmdlet…
Python was not found; run without arguments to install from the Microsoft Store…
```

## Files Read/Modified

None.
