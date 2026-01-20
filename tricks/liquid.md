---
title: Liquid Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/liquid/
---

### Create array in `.liquid`

```liquid
{% capture _list %}
1
2
3
{% endcapture %}
{% assign _list = _list | strip | split: '\n' %}
```

### Auto-format `.liquid` in VS Code / Cursor

1. Install [Prettier - Code formatter](https://marketplace.cursorapi.com/items/?itemName=esbenp.prettier-vscode)
2. Install [Shopify Liquid](https://marketplace.cursorapi.com/items/?itemName=Shopify.theme-check-vscode)

```json
# settings.json

    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    // Let VS Code to format its own .json settings
    "[jsonc]": {
        "editor.defaultFormatter": "vscode.json-language-features"
    },
    // Use Shopify formatter for .liquid only
    "[liquid]": {
        "editor.defaultFormatter": "Shopify.theme-check-vscode"
    }
```
