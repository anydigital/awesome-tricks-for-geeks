---
title: Zed  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/zed/
---

| Command | Action |
| --- | --- |
| Cmd + K | toggle AI Inline Assist |
| Cmd + Shift + I | toggle AI Agent Panel |
| Shift + Esc | toggle fullscreen |
| Ctrl + ` | toggle Terminal |

---

### Revert file to its staged version

Currently, Zed does not have a built-in "Restore to Staged" UI command. Most "revert" or "restore" actions in the Zed interface revert a file all the way back to the last commit (HEAD), which would wipe out your staged changes as well.

To revert a file to its staged version (discarding only the unstaged edits), you should use the terminal:
```sh
git restore PATH/TO/FILE.ext
```
