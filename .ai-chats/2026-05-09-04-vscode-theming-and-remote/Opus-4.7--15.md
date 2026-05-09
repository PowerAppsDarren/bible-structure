# Exchange 15: Cascadia Code still missing; embed font?

- **Timestamp:** 2026-05-09
- **Context:** User installed Apc but workbench still doesn't show Cascadia Code. Wonders whether to download from microsoft/cascadia-code GitHub repo and embed in this repo.

## User Input

> i still dont see the cascadia code font in the explorer. should we download that font from github.com/microsoft 's repo? and embed it into this repo?

## AI Response

Embedding the font in the repo won't help — VS Code's workbench (and the Apc extension) reads from **OS-installed fonts only**, not repo-local files. `@font-face` only works inside webviews (markdown preview, etc.), not the sidebar chrome.

**Two things to check first:**

1. **Is Cascadia Code actually installed on Windows?** PowerShell:
   ```powershell
   (New-Object System.Drawing.Text.InstalledFontCollection).Families | Where-Object { $_.Name -like "*Cascadia*" }
   ```
2. **Did you actually run `Enable Apc Extension`?** Just installing the extension does nothing — it has to patch VS Code (admin prompt + full quit/reopen).

**To install Cascadia Code system-wide** (if needed):
```powershell
winget install Microsoft.CascadiaCode
```
Or grab the latest release: https://github.com/microsoft/cascadia-code/releases — extract, install all `.ttf` files for all users.

Which is the missing piece — font not installed, or Apc not enabled?

## Tool Calls

- (none — diagnosis + suggestions only)

## Files Read/Modified

- (none)
