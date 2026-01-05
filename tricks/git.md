---
title: Git  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/git/
---

### Git Commit Email Privacy in 5 Minutes

Automatic no-reply email, `useConfigOnly`, and conditional `includeIf`:

[/tricks/git-commit-email-privacy/](/tricks/git-commit-email-privacy/)

<sup>✅ Guide by [TfG](/tricks/)</sup>


### Search the whole git history
```sh
git grep "SEARCH_FOR" $(git rev-list --all)
```

### Revert a file to its staged version (discarding only the unstaged edits)
```sh
git restore PATH_TO_FILE
```

### Restore a single file to its state from N commits ago
```sh
git restore PATH_TO_FILE --source=HEAD~N
```
(available in Git 2.23+)


#### Remove untracked files
```sh
# Dry Run (See what will be deleted):
git clean -fdn

# Remove untracked files and directories:
git clean -fd
```

### Smile 🤓

Git typo of the day:
```sh
git rest --hard
```
