# Exchange 11: Yes, wire up Apc extension

- **Timestamp:** 2026-05-09
- **Context:** User accepts the Apc approach. Mid-edit user adds "font weight: 600" via system-reminder.

## User Input

> yes
>
> (system-reminder mid-tool: "font weight: 600")

## AI Response

Settings added. To activate:

1. **Install the extension**: search Marketplace for **"Apc Customize UI++"** by *drcika* and install it.
2. **Enable it**: Command Palette → `Enable Apc Extension`. It'll prompt to patch VS Code's files (admin/restart needed).
3. Reload — the entire workbench (sidebar, tabs, status bar, command palette) will render in **Cascadia Code @ 600**.

Note: every time VS Code auto-updates, you'll need to re-run `Enable Apc Extension`. The extension shows a notification when that happens.

## Tool Calls

- `Edit` settings.json — added `apc.font.family`, `apc.monospace.font.family`
- `Edit` settings.json — added `apc.font.weight: "600"` (in response to mid-message reminder)

## Files Read/Modified

- `.vscode/settings.json`
