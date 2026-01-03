---
title: jsDelivr Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/jsdelivr/
---

#### Purge cache:

Purge the cache of a `@latest`, `@alpha` or similar to force your users to get the new updated version. Otherwise they might wait up to 7 days:

https://www.jsdelivr.com/tools/purge

Or manually by simply replacing <code>https://<big>cdn</big>.jsdelivr.net/...</code> to <code>//<big>purge</big>.</code>