---
title: Git  Tricks
site: tricks
type: tricks
---
[/tricks/git-commit-email-privacy/](/tricks/git-commit-email-privacy/)

`git grep "SEARCH_FOR" $(git rev-list --all)` -- search in whole git history

To restore a single file to its state from N commits ago, use the git restore command (available in Git 2.23+):
```sh
git restore --source=HEAD~N path/to/your/file.ext
```
