---
title: Git  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/git/
---

Git Commit Email Privacy in 5 Minutes using automatic no-reply email, `useConfigOnly`, and conditional `includeIf`:

[/tricks/git-commit-email-privacy/](/tricks/git-commit-email-privacy/)

<sup>✅ Recommended by TFG</sup>

---

Search the whole git history:
```sh
git grep "SEARCH_FOR" $(git rev-list --all)
```

---

Restore a single file to its state from N commits ago (available in Git 2.23+):
```sh
git restore --source=HEAD~N PATH/TO/YOUR/FILE.ext
```

---

## Smile 🤓

Git typo of the day:
```sh
git rest --hard
```
