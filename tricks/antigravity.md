---
title: Antigravity (A9y) Tricks <br><sup>(also for VS Code, Cursor, Windsurf & similar)</sup>
site: tricks
type: tricks
canonical: https://any.digital/tricks/antigravity/
reviewed: 2026-01-24
---

> A9y = Antigravity

For simplicity, let's call Antigravity as `A9y`, similar to `K8s` for Kubernetes.

---

## AI

### Enable Terminal Intellisense

- [A9y magic link](antigravity://settings/terminal.integrated.suggest.enabled)
- [Cursor magic link](cursor://settings/terminal.integrated.suggest.enabled)

Since A9y and Cursor are forks of VS Code, they support the same Terminal IntelliSense (dropdown completions) and adds its own AI-powered terminal features.

### Allow List Terminal Commands

```sh
ls
git status
git diff
git log
git show
```

---

## Focus

```sh
Cmd + B   # toggle left sidebar
Opt + Z   # toggle word wrap (useful in side-by-side diffs, markdown tables, ...)
```

### Better Zen Mode (inspired by Zed)

1. Override `View: Toggle Zen Mode` shortcut to: `Shift + Esc`
2. Turn Full Screen OFF: [A9y magic link](antigravity://settings/zenMode.fullScreen)
3. Turn Center Layout OFF: [A9y magic link](antigravity://settings/zenMode.centerLayout)

Done! Now you can quickly toggle Zen Mode with `Shift + Esc` w/o fullscreen and empty panels friction.

---

## Terminal

```sh
Cmd + J                   # toggle terminal
Ctrl + Opt + R            # loop through recent commands
clear                     # clear terminal
exit                      # kill/close terminal
agy YOUR_FILE_OR_FOLDER   # open file/folder in A9y
                          # to install: Shell Command: Install 'agy' command in PATH
```

---

## Editor

```sh
Opt + Up/Down           # move code
Shift + Opt + Up/Down   # duplicate code
Shift + Cmd + V         # open Markdown Preview
Cmd + P                 # jump to file
```

### Auto-formatting with Prettier

1. Install Prettier extension
2. Set it as default formatter: [A9y magic link](antigravity://settings/editor.defaultFormatter)

### Open Markdown Previews to the Side

By default `Shift + Cmd + V` opens preview in the same editor pane (which is annoying).

But you can re-map it to `Markdown: Open Preview to the Side` shortcut instead.

---

## Other

### Hide files, folders, symlinks

```json {data-caption=YOUR_PROJECT/.vscode/settings.json}
{
  "files.exclude": {
    "YOUR_FILE_OR_FOLDER": true
  },
  "search.followSymlinks": false
}
```

## The A9y Easter Egg

If you have Python installed, you can trigger this feature by typing the following into your terminal or script:

```python
import antigravity
```

### What it does:

- **Web Redirection:** Running this command opens your web browser to the classic **XKCD comic #353**, which depicts a programmer flying because Python is so easy to use.
- **The "geohashing" Library:** Within the `antigravity.py` module, there is an implementation of the XKCD Geohashing algorithm, which allows users to find a random location nearby to meet up based on the day's Dow Jones Industrial Average.

---

Btw, did you know that:

> Google paid $2.4 billion for Antigravity
> to _license Windsurf IDE forked from VS Code built by_{.ml-2 .text-xs}
> Microsoft.
