---
title: Nunjucks & Liquid Tricks <sub>for Eleventy, Shopify, Jekyll etc.</sub>
site: tricks
type: tricks
canonical: https://any.digital/tricks/njk-liquid/
includes:
  - path: https://raw.githubusercontent.com/anydigital/bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/bricks/README.md
    section: njk-liquid
---

## First Things First

<!--section:11ty-basics-->

### Syntax highlighting <small>in [VS Code~editors](/tricks/antigravity/)</small>

#### `.njk` {#njk-vscode}

- 🧩 Install https://github.com/edheltzel/better-nunjucks-for-visual-studio-code

This is a modern fork of the original extension. It is specifically designed to solve the "11ty problem" where you mix Nunjucks and HTML.

**Why it's better:** It injects Nunjucks grammar directly into the standard HTML grammar. This means you get full Nunjucks highlighting and the editor still knows it's an HTML file, giving you better Emmet and CSS autocompletion.

**No Config:** It works out of the box without needing to manually map file associations in your settings.

#### `.liquid`

- 🧩 Install https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode

### Auto-formatting <small>in [VS Code~editors](/tricks/antigravity/)</small>

1. 🧩 Install https://github.com/prettier/prettier-vscode (if not yet)

#### `.njk`

2. Install a compatible Prettier plugin for your project, for example:

```sh
npm i -D prettier-plugin-jinja-template
```

3. It might be tricky to find a well-maintained Nunjucks plugin, but `jinja-template` works just fine with `.njk` via `.html` override:

```json {data-caption=.prettierrc.json}
{
  "plugins": ["prettier-plugin-jinja-template"],
  "overrides": [
    {
      "files": ["*.njk", "*.html"],
      "options": {
        "parser": "jinja-template"
      }
    }
  ]
}
```

`PRO TIP:` If you already use https://github.com/anydigital/bricks, it’s even easier. You can simply:

```sh
ln -s ./node_modules/@anydigital/bricks/.prettierrc.json
```

#### `.liquid`

2. 🧩 Install https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode (same extension for both highlighting and formatting)

##### How to prevent unclosed html tags from breaking auto-formatting?

`{% # prettier-ignore %}` might not help with that, because the parser crashes on the "broken" HTML before it even reads the ignore command.

But there is a trick with "fake" `{% if true %}` condition:

```liquid {data-caption=_html-begin.liquid}
{% if true %}<html>{% endif %}
<head>
  ...
</head>
{% if true %}<body>{% endif %}
  ...
```

```liquid {data-caption=_html-end.liquid}
{% if true %}</body><html>{% endif %}
```

This "fake conditional" trick is a clever way to bypass the Abstract Syntax Tree (AST) parsers used by formatters like Prettier. Since the formatter sees the tag wrapped in a logic block, it often treats the HTML as a string or a partial fragment rather than a structural error.

<!--section:other-->

---

## Tricks

### Create array

```liquid {data-caption=.liquid}
{% capture _new_array %}
1
2
3
{% endcapture %}
{% assign _new_array = _new_array | strip | split: '\n' %}
```

### Sort array by attribute

Per official `.njk` documentation:

> **sort(arr, reverse, caseSens, attr)**  
> Sort arr with JavaScript's arr.sort function. If reverse is true, result will be reversed. Sort is case-insensitive by default, but setting caseSens to true makes it case-sensitive. If attr is passed, will compare attr from each item.

But you can actually do this trick:

```jinja2 {data-caption=.njk}
{% for item in array | sort(attribute='weight') %}
  ...
{% endfor %}
```

### Include and render `.md` file w/o its Front Matter <small>(11ty-only)</small>

```jinja2 {data-caption=.njk}
{# first, get the raw content using `html` as plain-text engine #}
{% set _eval = "{% renderFile './YOUR_FILE.md', {}, 'html' %}" %}
{% set _raw_md = _eval | renderContent('njk') %}

{# then, remove the front matter using regex, and render using `md` #}
{{ _raw_md | replace(r/^---[\s\S]*?---/, '') | renderContent('md') | safe }}
```

---

## `PS:` Beware: False Positives in `.liquid`

In Liquid templating, a "false positive" usually occurs when a value you expect to be **falsy** (like an empty string or zero) is actually treated as **truthy** by the Liquid engine.

Unlike languages like JavaScript or Python, Liquid has very specific rules for truthiness.

### The "Everything is Truthy" Rule

In Liquid, **only** `false` and `nil` (null) are falsy. Every other value evaluates to `true` in a conditional statement.

Common Pitfalls:

| Value               | Liquid Result | Why?                                            |
| ------------------- | ------------- | ----------------------------------------------- |
| `""` (Empty String) | **Truthy**    | An empty string is still a "present" object.    |
| `0` (Zero)          | **Truthy**    | Numbers are always truthy, regardless of value. |
| `[]` (Empty Array)  | **Truthy**    | An empty collection is not `nil`.               |

### How to Avoid False Positives

To prevent these values from triggering your `if` statements, you should check for size or specific content rather than just the variable itself.

The Right Way vs. The Wrong Way:

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

### The `blank` and `empty` Keywords

Liquid provides special keywords to handle these cases gracefully:

- **`blank`**: Returns true if the value is `nil`, `false`, an empty string, or a string containing only whitespace.
- **`empty`**: Returns true if the value is an empty string, empty array, or empty hash.

> **Note:** These are often used with the `unless` tag or the `!=` operator to ensure you are working with meaningful data.

---

- Featured in https://11tybundle.dev/categories/nunjucks-macros/
- See also https://any.digital/tricks/11ty/
