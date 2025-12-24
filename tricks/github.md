---
title: GitHub Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/github/
---

Hidden feature in GitHub web editor: you can move a line of code up or down by holding Option (on Mac) or Alt (on Windows/Linux) and pressing the Up or Down arrow keys!

<sup>✅ Discovered by TFG</sup>

---

Automatically sync code snippets in your README with GitHub Actions:

https://www.reddit.com/r/TricksForGeeks/comments/1pk9wr6/automatically_sync_code_snippets_in_your_readme/

<sup>✅ Guide by TFG</sup>

---

Generate a license for your repo:
```sh
brew install gh
# This pulls the legal text from GitHub's API and saves it as a file
gh repo license view CC-BY-SA-4.0 > LICENSE
```
<sup>✅ Verified by TFG</sup>
