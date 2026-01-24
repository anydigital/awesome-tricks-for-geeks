---
title: Markdown Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/md/
---

## `markdown-it-attrs`

### Long-long links with many-many CSS classes, but readable

```md
[Suggest a Page<i class="fa-brands fa-github ml-1"></i>
](https://github.com/anydigital/awesome-tricks-for-geeks/new/main/tricks
){.text-slate-500 .font-light .decoration-dashed}
```

It works with lists too!

```md
- [Suggest a Page<i class="fa-brands fa-github ml-1"></i>
  ](https://github.com/anydigital/awesome-tricks-for-geeks/new/main/tricks
  ){.text-slate-500 .font-light .decoration-dashed} {.list-none}
```
