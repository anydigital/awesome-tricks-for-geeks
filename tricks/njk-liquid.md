---
title: Nunjucks & Liquid Tricks <sub>for Eleventy, Shopify, Jekyll etc.</sub>
site: tricks
type: tricks
canonical: https://any.digital/tricks/njk-liquid/
includes:
  - #
    # path: https://raw.githubusercontent.com/anydigital/bricks/refs/heads/main/README.md
    path: ../node_modules/@anydigital/bricks/README.md
    section: njk-liquid
  - path: tricks/_njk-liquid-specific.md
  - #
    # path: https://raw.githubusercontent.com/anydigital/eleventy-bricks/refs/heads/main/README.md
    path: ../node_modules/@anydigital/eleventy-bricks/README.md
    section: filters
  - text: "Featured in https://11tybundle.dev/categories/nunjucks-macros/"
---

## First Things First

|                  | `.njk`                                                             | `.liquid`                                             |
| ---------------- | ------------------------------------------------------------------ | ----------------------------------------------------- |
| Docs             | https://mozilla.github.io/nunjucks/templating.html                 | https://shopify.github.io/liquid/basics/introduction/ |
| Built-in Filters | https://mozilla.github.io/nunjucks/templating.html#builtin-filters | https://shopify.github.io/liquid/#filters-section     |

### Syntax highlighting <sub>in [VS Code~editors](/tricks/antigravity/)</sub>

#### `.njk` {#njk-vscode}

- 🧩 Install https://github.com/edheltzel/better-nunjucks-for-visual-studio-code

This is a modern fork of the original extension. It is specifically designed to solve the "11ty problem" where you mix Nunjucks and HTML.

**Why it's better:** It injects Nunjucks grammar directly into the standard HTML grammar. This means you get full Nunjucks highlighting and the editor still knows it's an HTML file, giving you better Emmet and CSS autocompletion.

**No Config:** It works out of the box without needing to manually map file associations in your settings.

#### `.liquid`

- 🧩 Install https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode

### Auto-formatting <sub>in [VS Code~editors](/tricks/antigravity/)</sub>

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

2. 🧩 Install https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode (2-in-1 extension for highlighting + formatting)

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

---
