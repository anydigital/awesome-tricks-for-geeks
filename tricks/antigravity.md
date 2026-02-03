---
title: "Antigravity Tricks <sub>& VS Code~editors (Cursor, Windsurf etc.)</sub>"
site: tricks
type: tricks
canonical: https://any.digital/tricks/antigravity/
revised: 2026-02-01
---

---

> A9y = Antigravity

For simplicity, let's call Antigravity as `A9y`, similar to `K8s` for Kubernetes.

---

## AI <small>Tricks</small>

### 🆕 Enabling Sandboxing

You can enable or disable sandboxing in Antigravity User Settings. Toggle "Enable Terminal Sandboxing" to turn sandboxing on or off. When enabled, you can also control network access separately using the "Sandbox Allow Network" toggle.

https://antigravity.google/docs/sandbox-mode

### Enable Terminal Intellisense

- [A9y magic link](antigravity://settings/terminal.integrated.suggest.enabled)
- [Cursor magic link](cursor://settings/terminal.integrated.suggest.enabled)

Since A9y and Cursor are forks of VS Code, they support the same Terminal IntelliSense (dropdown completions) and adds its own AI-powered terminal features.

### Allow List Terminal Commands

```sh
ls
find
grep
git status
git diff
git log
git show
npm test
```

---

## Keep Focus

| Command   | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| `Cmd + B` | toggle left sidebar                                                   |
| `Opt + Z` | toggle word wrap (useful in side-by-side diffs, markdown tables, ...) |

### 🥷 Better Zen Mode (inspired by Zed)

1. Override `View: Toggle Zen Mode` shortcut to: `Shift + Esc`
2. Turn Full Screen OFF: [A9y magic link](antigravity://settings/zenMode.fullScreen)
3. Turn Center Layout OFF: [A9y magic link](antigravity://settings/zenMode.centerLayout)

Done! Now you can quickly toggle Zen Mode with `Shift + Esc` w/o fullscreen and empty panels friction.

---

## Terminal <small>Commands</small>

| Command          | Description                                                                       |
| ---------------- | --------------------------------------------------------------------------------- |
| `Cmd + J`        | toggle terminal                                                                   |
| `Ctrl + Opt + R` | loop through recent commands                                                      |
| `clear`          | clear terminal                                                                    |
| `exit`           | kill/close terminal                                                               |
| `agy <path>`     | open file/folder in A9y (install: `Shell Command: Install 'agy' command in PATH`) |

---

## Editing <small>Tricks</small>

| Command                 | Description           |
| ----------------------- | --------------------- |
| `Opt + Up/Down`         | move code             |
| `Shift + Opt + Up/Down` | duplicate code        |
| `Shift + Cmd + V`       | open Markdown Preview |
| `Cmd + P`               | jump to file          |

### Auto-formatting with Prettier

1. 🧩 Install https://github.com/prettier/prettier-vscode
2. ⚙️ Set it as default formatter:
   - [A9y magic link](antigravity://settings/editor.defaultFormatter)
   - [Cursor magic link](cursor://settings/editor.defaultFormatter)
   - [VS Code magic link](vscode://settings/editor.defaultFormatter)

### Open Markdown Previews to the Side

By default `Shift + Cmd + V` opens preview in the same editor pane (which is annoying).

But you can re-map it to `Markdown: Open Preview to the Side` shortcut instead.

---

## Other <small>Tricks</small>

### Hide files, folders, symlinks

```json {data-caption=YOUR_PROJECT/.vscode/settings.json}
{
  "files.exclude": {
    "YOUR_FILE_OR_FOLDER": true
  },
  "search.followSymlinks": false
}
```

### The A9y Easter Eggs

If you have Python installed, you can trigger this feature by typing the following into your terminal:

```sh
python3 -c "import antigravity"
```

Running this command opens your web browser to the classic [XKCD comic #353](https://xkcd.com/353/), which depicts a programmer flying because Python is so easy to use:

![](https://imgs.xkcd.com/comics/python.png)

#### The Egg inside the Egg

The `antigravity` module is a famous Python "Easter egg." While most people know it for opening the XKCD "Python" comic in your browser when imported, it contains a second "egg inside the egg": a functional implementation of the **Munroe Algorithm** (Geohashing).

**How it Works:** The algorithm, described in [XKCD #426](https://xkcd.com/426/), generates a set of random coordinates for every area (graticule) on Earth each day. To ensure the locations are unpredictable until the day of, the algorithm uses the most recent **Dow Jones Industrial Average** opening price as a "salt" for the hash.

![](https://imgs.xkcd.com/comics/geohashing.png)

It has been included in the CPython standard library since version 2.7 and 3.1.

**But Why?** The original idea was to encourage people to get outside and meet at a random, algorithmically-generated spot in their local area.

---

## See Also

- https://any.digital/insights/ai-ide/
