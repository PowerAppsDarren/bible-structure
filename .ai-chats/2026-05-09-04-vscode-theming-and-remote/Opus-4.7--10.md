# Exchange 10: Cascadia Code in explorer? (no native)

- **Timestamp:** 2026-05-09
- **Context:** User wants Cascadia Code as the explorer/sidebar font.

## User Input

> can we use cascadia code for the font for explorer?

## AI Response

Not natively — VS Code doesn't expose a font setting for the sidebar/explorer. `editor.fontFamily` only affects the editor; `terminal.integrated.fontFamily` only the terminal. No `sideBar.fontFamily` exists.

Two workarounds:

1. **Extension: "Apc Customize UI++"** — adds `apc.font.family` so you can set workbench font globally. Requires enabling Electron customization (the extension walks you through it).

2. **Custom CSS** (via "Custom CSS and JS Loader" extension) — inject:
   ```css
   .monaco-workbench .part.sidebar { font-family: "Cascadia Code" !important; }
   ```

Both modify VS Code's installed files, so they re-prompt after each VS Code update. Want me to wire up option 1 in settings (you'd still need to install the extension)?

## Tool Calls

- (none — explanation only)

## Files Read/Modified

- (none)
