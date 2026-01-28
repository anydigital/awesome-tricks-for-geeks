---
title: Liquid Tricks <small>for 11ty, Shopify etc.</small>
site: tricks
type: tricks
canonical: https://any.digital/tricks/liquid/
reviewed: 2026-01-21
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

#### Auto-formating for open (non-closed) tags

```liquid
{% # if-true trick not to break auto-formatting %}
{% if true %}<body>{% endif %}
```

## Beware: False Positives

In Liquid templating, a "false positive" usually occurs when a value you expect to be **falsy** (like an empty string or zero) is actually treated as **truthy** by the Liquid engine.

Unlike languages like JavaScript or Python, Liquid has very specific rules for truthiness.

---

### 1. The "Everything is Truthy" Rule

In Liquid, **only** `false` and `nil` (null) are falsy. Every other value evaluates to `true` in a conditional statement.

#### Common Pitfalls

| Value               | Liquid Result | Why?                                            |
| ------------------- | ------------- | ----------------------------------------------- |
| `""` (Empty String) | **Truthy**    | An empty string is still a "present" object.    |
| `0` (Zero)          | **Truthy**    | Numbers are always truthy, regardless of value. |
| `[]` (Empty Array)  | **Truthy**    | An empty collection is not `nil`.               |

---

### 2. How to Avoid False Positives

To prevent these values from triggering your `if` statements, you should check for size or specific content rather than just the variable itself.

#### The Right Way vs. The Wrong Way

- **Wrong:**

```liquid
{% if my_string %} This will always show if the string exists, even if empty. {% endif %}
```

- **Right (Checking for content):**

```liquid
{% if my_string != blank %} This only shows if there is actual text. {% endif %}
```

- **Right (Checking arrays/strings by size):**

```liquid
{% if my_array.size > 0 %} This ensures the list isn't empty. {% endif %}
```

---

### 3. The `blank` and `empty` Keywords

Liquid provides special keywords to handle these cases gracefully:

- **`blank`**: Returns true if the value is `nil`, `false`, an empty string, or a string containing only whitespace.
- **`empty`**: Returns true if the value is an empty string, empty array, or empty hash.

> **Note:** These are often used with the `unless` tag or the `!=` operator to ensure you are working with meaningful data.
