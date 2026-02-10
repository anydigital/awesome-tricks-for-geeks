## Nunjucks-Specific <small>Tricks</small>

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

## Liquid-Specific <small>Tricks</small>

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

In Liquid templating, a "false positive" usually occurs when a value you expect to be **falsy** (like an empty string or zero) is actually treated as **truthy** by the Liquid engine.

Unlike languages like JavaScript or Python, Liquid has very specific rules for truthiness.

#### The "Everything is Truthy" Rule

In Liquid, **only** `false` and `nil` (null) are falsy. Every other value evaluates to `true` in a conditional statement.

Common Pitfalls:

| Value               | Liquid Result | Why?                                            |
| ------------------- | ------------- | ----------------------------------------------- |
| `""` (Empty String) | **Truthy**    | An empty string is still a "present" object.    |
| `0` (Zero)          | **Truthy**    | Numbers are always truthy, regardless of value. |
| `[]` (Empty Array)  | **Truthy**    | An empty collection is not `nil`.               |

#### How to Avoid False Positives

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

#### The `blank` and `empty` Keywords

Liquid provides special keywords to handle these cases gracefully:

- **`blank`**: Returns true if the value is `nil`, `false`, an empty string, or a string containing only whitespace.
- **`empty`**: Returns true if the value is an empty string, empty array, or empty hash.

> **Note:** These are often used with the `unless` tag or the `!=` operator to ensure you are working with meaningful data.

---

## 11ty-Specific <small>Tricks</small>

<!--section:11ty-->

### Include and render `.md` file w/o its Front Matter

```jinja2 {data-caption=.njk}
{# first, get the raw content using `html` as plain-text engine #}
{% set _eval = "{% renderFile './YOUR_FILE.md', {}, 'html' %}" %}
{% set _raw_md = _eval | renderContent('njk') %}

{# then, remove the front matter using regex, and render using `md` #}
{{ _raw_md | replace(r/^---[\s\S]*?---/, '') | renderContent('md') | safe }}
```
