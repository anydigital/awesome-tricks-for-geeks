---
title: Cursor Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/cursor/
---

### Enable Terminal IntelliSense

cursor://settings/terminal.integrated.suggest.enabled

Since Cursor is a fork of VS Code, it supports the same Terminal IntelliSense (dropdown completions) and adds its own AI-powered terminal features.

<sup>✅ Recommended by [TfG](/tricks/)</sup>


### View: Toggle Zen Mode (inspired by Zed)

```json
{
  "key": "shift+escape",
  "command": "workbench.action.toggleZenMode",
  ...
}
```


### Markdown: Open Preview to the Side

```json
{
  "key": "shift+cmd+v",
  "command": "markdown.showPreviewToSide",
  ...
}
```


### Shortcuts

| Command | Action |
| --- | --- |
| <big>AI:</big> ||
| Cmd + K | edit/generate inline with AI |
| Cmd + L	| toggle AI Chat |
| <big>Focus Mode:</big> ||
| Shift + Esc <br><sup>(custom)</sup> | switch to Zen mode <br>- especially useful for side-by-side diffs <br>- recommended Preferences: Open User Settings > Zen Mode: Center Layout OFF |
| Cmd + B | toggle left sidebar |
| <big>Other:</big> ||
| Opt + Up/Down | move code |
| Shift + Cmd + V <br><sup>(custom)</sup> | edit Markdown with side preview |
| <big>Integrated Terminal:</big> ||
| Cmd + J | toggle terminal |
| Ctrl + Opt + R | loop through recent commands |
| `cursor FILE_OR_FOLDER` | open file/folder in Cursor |


### Hide files, folders and/or symlinks

```json
# .vscode/settings.json:
{
  "search.followSymlinks": false,
  "files.exclude": {
    "FILE_OR_FOLDER": true
  }
}
```

### Clear/kill terminals

If you are currently typed into the terminal, simply type:
```sh
clear
# or
exit
```
This will clear or close the session and, in most cases, remove the terminal instance from your list.


### Auto-formatting on save with Prettier

`settings.json`:
```json
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true,
    "[jsonc]": {
        "editor.defaultFormatter": "vscode.json-language-features"
    }
```
(keeping built-in formatting for IDE settings)
