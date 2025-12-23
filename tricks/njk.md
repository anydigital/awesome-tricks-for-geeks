---
title: Nunjucks Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/njk/
---

## Sort array by attribute

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
<sup>✅ Verified by TFG</sup>

---

Q&A: https://www.reddit.com/r/eleventy/ (yes, they help with Nunjucks!)
