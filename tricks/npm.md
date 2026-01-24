---
title: npm  Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/npm/
reviewed: 2026-01-18
---

### npm link auto-completion with @namespaces support

`~/.zshrc`:

```
# Initialize zsh completion system
autoload -Uz compinit
compinit

# Enable npm link completion for scoped packages
_npm_link_completion() {
  local -a pkgs
  pkgs=($(
    {
      find -L "$(npm root -g)" -mindepth 1 -maxdepth 1 -type d ! -name "@*"; \
      find -L "$(npm root -g)/@"* -mindepth 1 -maxdepth 1 -type d; \
    } | sed "s|$(npm root -g)/||"
  ))
  _describe 'npm packages' pkgs
}

# Enable completion for 'npm link'
compdef _npm_link_completion npm link
```

### [Purge cache on jsDelivr CDN](/tricks/jsdelivr/#purge-cache)
