---
title: Terminal / Shell / CLI Tips & Tricks for Developers
site: tricks
type: tricks
canonical: https://any.digital/tricks/terminal/
---

#### Check HTTP headers with `curl`

```sh
curl --head HTTP_URL
# or simply:
curl -I HTTP_URL
```
The `-I` flag (shorthand for `--head`) fetches only the HTTP headers from a server. This is the fastest way to inspect status codes, content types, and server metadata without downloading the actual page content.
