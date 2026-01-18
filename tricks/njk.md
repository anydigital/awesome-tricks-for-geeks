---
title: Nunjucks Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/njk/
---

### Sort array by attribute

Per official documentation:

> **sort(arr, reverse, caseSens, attr)**
> 
> Sort arr with JavaScript's arr.sort function. If reverse is true, result will be reversed. Sort is case-insensitive by default, but setting caseSens to true makes it case-sensitive. If attr is passed, will compare attr from each item.

But you can actually do this trick:
```njk
{% for item in array | sort(attribute='weight') %}
...
{% endfor %}
```


### .njk syntax highlighting in [Cursor / VS Code](/tricks/cursor/)

https://github.com/edheltzel/better-nunjucks-for-visual-studio-code

This is a modern fork of the original extension. It is specifically designed to solve the "11ty problem" where you mix Nunjucks and HTML.

Best for: 11ty developers using Cursor/VS Code.

Why it's better: It injects Nunjucks grammar directly into the standard HTML grammar. This means you get full Nunjucks highlighting and the editor still knows it's an HTML file, giving you better Emmet and CSS autocompletion.

No Config: It works out of the box without needing to manually map file associations in your settings.

### .njk code formatting in [Cursor / VS Code](/tricks/cursor/) globally

```sh
npm i -g prettier-plugin-twig-nunjucks-melody
```

```json
# ~/.prettierrc.json
{
  "plugins": ["/opt/homebrew/lib/node_modules/prettier-plugin-twig-nunjucks-melody"]
}
```

### Resources

- https://www.reddit.com/r/eleventy/ for Q&A (yes, they help with Nunjucks!)
