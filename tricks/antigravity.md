---
title: "Antigravity Tricks <sub>& VS Code~editors (Cursor, Windsurf etc.)</sub>"
site: tricks
type: tricks
canonical: https://any.digital/tricks/antigravity/
revised: 2026-02-04
---

---

> A9y = Antigravity

For simplicity, let's call Antigravity as `A9y`, similar to `K8s` for Kubernetes.

---

## AI <small>Tricks</small>

In **A9y** (Antigravity IDE), the AI is designed to be agentic, meaning it doesn't just suggest text but can actually execute tasks across your editor, terminal, and browser.

### 🆕 Enabling Sandboxing

You can enable or disable sandboxing in Antigravity User Settings. Toggle "Enable Terminal Sandboxing" to turn sandboxing on or off. When enabled, you can also control network access separately using the "Sandbox Allow Network" toggle.

https://antigravity.google/docs/sandbox-mode

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

### Enable Terminal Intellisense

- [A9y magic link](antigravity://settings/terminal.integrated.suggest.enabled)
- [Cursor magic link](cursor://settings/terminal.integrated.suggest.enabled)

Since A9y and Cursor are forks of VS Code, they support the same Terminal IntelliSense (dropdown completions) and adds its own AI-powered terminal features.

### AI Shortcuts

Here are the top AI commands and shortcuts to master the workflow:

| Command                                | Action                                                                                                |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `Cmd + I`                              | Inline AI                                                                                             |
| `Cmd + L` <sub>`Cmd + Shift + L`</sub> | Agent Panel/Chat <sub>open new</sub>                                                                  |
| `Cmd + E`                              | **Mode Switch:** Quickly toggle between **Fast** (quick edits) and **Planning** (complex tasks) modes |
| `Tab`                                  | Accept ghost-text suggestions                                                                         |

### Powerful Slash `/` & Context `@` Commands

In the **Agent Panel**, use these to refine your requests:

- `/test`: A workflow command to automatically generate and run unit tests for the active file.
- `/review`: Initiates a deep-scan of your current changes to check for bugs or DRY (Don't Repeat Yourself) violations.
- `@YOUR_FILE`: Explicitly attach specific files or folders to the AI's context window so it "sees" the relevant code.
- `@browser`: Invokes the Browser Agent to verify UI changes or scrape documentation.

### Agent Rules <sub>`.agent/rules/`</sub>

You can automate your own "commands" by adding `.md` files to the `.agent/rules/` directory. For example, a rule saying "Always use TypeScript strict mode" acts as a permanent background command that the AI follows without you having to ask every time.

#### How to configure A9y AI globally to always prefer `git mv` for moving/renaming files?

1. Open A9y and press `Cmd + Shift + P` (or `Ctrl + Shift + P`).
2. Search for **"Antigravity: Open User Customizations"**.
3. In the `Global Instructions` text area, append:
`"Preference: Always use 'git mv' for file relocations and renames."`
4. Save and restart your session.

---

## Keeping Focus

| Command   | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| `Cmd + B` | toggle left sidebar                                                   |
| `Opt + Z` | toggle word wrap (useful in side-by-side diffs, markdown tables, ...) |

### 🥷 Better Zen Mode (inspired by Zed)

1. Override `View: Toggle Zen Mode` shortcut to: `Shift + Esc`
2. Turn Full Screen OFF: [A9y magic link](antigravity://settings/zenMode.fullScreen)
3. Turn Center Layout OFF: [A9y magic link](antigravity://settings/zenMode.centerLayout)
4. Unhide line numbers: [A9y magic link](antigravity://settings/zenMode.hideStatusBar)

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

| Command                 | Description                |
| ----------------------- | -------------------------- |
| `Opt + Up/Down`         | move code                  |
| `Shift + Opt + Up/Down` | duplicate code             |
| `Shift + Cmd + V`       | open Markdown Preview      |
| `Cmd + P`               | jump to file               |
| `Shift + Opt + I`       | activate multi-line cursor |

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

### Comparing two files (diffing)

In **A9y**, comparing two files (Diffing) is straightforward and can be handled via the UI or the integrated terminal.

Using the UI (Side Bar):

1. Open the **Explorer** view in the left sidebar.
2. **Right-click** the first file and select **Select for Compare**.
3. **Right-click** the second file and select **Compare with Selected**.
4. A side-by-side diff editor will open, highlighting additions (green) and deletions (red).

Using the Command Line:

```sh
agy --diff FILE1 FILE2
```

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
