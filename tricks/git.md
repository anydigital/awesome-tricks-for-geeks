---
title: Git  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/git/
---

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

### Remove untracked files

```sh
git clean -i
```

---

## GitHub <small>Tricks</small>

### GitHub web editor

Hidden feature in GitHub web editor: you can move a line of code up or down by holding Option (on Mac) or Alt (on Windows/Linux) and pressing the Up or Down arrow keys!

### Automatically sync code snippets in your README with GitHub Actions

https://www.reddit.com/r/TricksForGeeks/comments/1pk9wr6/automatically_sync_code_snippets_in_your_readme/

### Generate a license for your repo

```sh
brew install gh
# This pulls the legal text from GitHub's API and saves it as a file
gh repo license view CC-BY-SA-4.0 > LICENSE
```

### Cool stuff

- https://github.com/anuraghazra/github-readme-stats

---

## `PS:` Smile 🤓

Git typo of the day:

```sh
git rest --hard
```
