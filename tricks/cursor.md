---
title: Cursor Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/cursor/
---

#### Enable Terminal IntelliSense:

cursor://settings/terminal.integrated.suggest.enabled

Since Cursor is a fork of VS Code, it supports the same Terminal IntelliSense (dropdown completions) and adds its own AI-powered terminal features.

<sup>✅ Recommended by TFG</sup>

#### View: Toggle Zen Mode (inspired by Zed)

```json
{
  "key": "shift+escape",
  "command": "workbench.action.toggleZenMode",
  ...
}
```

#### Markdown: Open Preview to the Side

```json
{
  "key": "shift+cmd+v",
  "command": "markdown.showPreviewToSide",
  ...
}
```

#### Shortcuts

| Command | Action |
| --- | --- |
| ***Terminal:*** |  |
| Ctrl + \` | toggle terminal |
| Ctrl + Opt + R | loop through recent commands |
