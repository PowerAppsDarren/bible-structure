# Exchange 02: Cascadia Code font + weight 600

- **Timestamp:** 2026-05-09
- **Context:** Continuing terminal theming. User wants Cascadia Code font with weight 600 and asks whether they need to download it from Microsoft's GitHub.

## User Input

> change the terminal font to cascadia code. do we need to download it from github.com from microsoft profile? we need font-weight to be set to 600.

## AI Response

Cascadia Code ships with VS Code by default — no download needed. (It's also bundled with Windows Terminal and recent Windows builds.) If for some reason it's missing, you can grab it from https://github.com/microsoft/cascadia-code/releases, but try the settings first.

Done. Set `terminal.integrated.fontFamily` to `Cascadia Code` and `terminal.integrated.fontWeight` to `600`.

## Tool Calls

**Edit** → `.vscode/settings.json`

Final file contents:

```json
{
  "workbench.colorCustomizations": {
    "terminal.background": "#171717",
    "terminal.foreground": "#00FF00"
  },
  "terminal.integrated.fontFamily": "Cascadia Code",
  "terminal.integrated.fontWeight": 600
}
```

## Function Results

Edit applied successfully.
