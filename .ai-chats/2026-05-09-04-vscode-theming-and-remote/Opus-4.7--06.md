# Exchange 06: Wire up markdown.css preview stylesheet

- **Timestamp:** 2026-05-09
- **Context:** User accepts the markdown preview CSS option.

## User Input

> sure

## AI Response

Done. Created `.vscode/markdown.css` and registered it in settings via a workspace-relative path.

Open any `.md` file → **Ctrl+Shift+V** for preview (or **Ctrl+K V** for side-by-side). You'll see:

- Padded paragraphs and list items
- Inline code as amber pills with padding
- Fenced blocks in a bordered box with breathing room
- Blockquotes with cyan left-border
- Padded table cells

Tweak any value in `markdown.css` and the preview live-reloads.

## Tool Calls

- `Write` `.vscode/markdown.css` — full stylesheet (body padding, p/li padding, code pills, pre blocks, blockquote, headings, table cells)
- `Edit` `.vscode/settings.json` — add `"markdown.styles": ["markdown.css"]`

## Files Read/Modified

- Created: `.vscode/markdown.css`
- Modified: `.vscode/settings.json`
