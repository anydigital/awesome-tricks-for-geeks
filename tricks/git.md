---
title: Git  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/git/
---
[/tricks/git-commit-email-privacy/](/tricks/git-commit-email-privacy/)

Search the whole git history:
```sh
git grep "SEARCH_FOR" $(git rev-list --all)
```
<sup>✅ Verified by TFG</sup>

To restore a single file to its state from N commits ago, use the git restore command (available in Git 2.23+):
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
