---
title: Git  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/git/
---

Git Commit Email Privacy in 5 Minutes:  
(automatic no-reply email, `useConfigOnly`, and conditional `includeIf`)

[/tricks/git-commit-email-privacy/](/tricks/git-commit-email-privacy/)

---

Search the whole git history:
```sh
git grep "SEARCH_FOR" $(git rev-list --all)
```
<sup>✅ Verified by TFG</sup>

---

Restore a single file to its state from N commits ago (available in Git 2.23+):
```sh
git restore --source=HEAD~N PATH/TO/YOUR/FILE.ext
```
<sup>✅ Verified by TFG</sup>

---

## Smile 🤓

Git typo of the day:
```sh
git rest --hard
```
