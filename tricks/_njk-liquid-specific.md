## Liquid-Specific <small>Tricks</small>

- https://shopify.github.io/liquid/basics/introduction/
- https://shopify.github.io/liquid/#filters-section

### Syntax highlighting & auto-formatting <sub>in [VS Code~editors](/tricks/antigravity/)</sub> {#liquid-vscode}

1. 🧩 Install https://github.com/prettier/prettier-vscode (if not yet)
2. 🧩 Install https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode  
   (2-in-1 extension for highlighting & formatting)

This is a huge advantage for `.liquid` over `.njk` so far.

### Prevent unclosed html tags from breaking auto-formatting

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

### Create array

```liquid {data-caption=.liquid}
{% capture _new_array %}
1
2
3
{% endcapture %}
{% assign _new_array = _new_array | strip | split: '\n' %}
```

### Beware: False Positives <small>in `.liquid`</small>

- https://liquidjs.com/tutorials/truthy-and-falsy.html
- https://www.11ty.dev/docs/languages/liquid/#java-script-truthiness-in-liquid

❌ Wrong:

```liquid
{% if my_string %} This will always show if the string exists, even if empty. {% endif %}
```

✅ Right (Checking for content):

```liquid
{% if my_string != blank %} This only shows if there is actual text. {% endif %}
```

✅ Right (Checking arrays/strings by size):

```liquid
{% if my_array.size > 0 %} This ensures the list isn't empty. {% endif %}
```

---

## Nunjucks-Specific <small>Tricks</small>

- https://mozilla.github.io/nunjucks/templating.html
- https://mozilla.github.io/nunjucks/templating.html#builtin-filters

### Syntax highlighting <sub>in [VS Code~editors](/tricks/antigravity/)</sub> {#njk-vscode}

- 🧩 Install https://github.com/edheltzel/better-nunjucks-for-visual-studio-code

This is a modern fork of the original extension. It is specifically designed to solve the "11ty problem" where you mix Nunjucks and HTML.

**Why it's better:** It injects Nunjucks grammar directly into the standard HTML grammar. This means you get full Nunjucks highlighting and the editor still knows it's an HTML file, giving you better Emmet and CSS autocompletion.

**No Config:** It works out of the box without needing to manually map file associations in your settings.

### Auto-formatting <sub>in [VS Code~editors](/tricks/antigravity/)</sub>

1. 🧩 Install https://github.com/prettier/prettier-vscode (if not yet)

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

---

## 11ty-Specific <small>Tricks</small>

### Include and render `.md` file w/o its Front Matter

```jinja2 {data-caption=.njk}
{# first, get the raw content using `html` as plain-text engine #}
{% set _eval = "{% renderFile './YOUR_FILE.md', {}, 'html' %}" %}
{% set _raw_md = _eval | renderContent('njk') %}

{# then, remove the front matter using regex, and render using `md` #}
{{ _raw_md | replace(r/^---[\s\S]*?---/, '') | renderContent('md') | safe }}
```
