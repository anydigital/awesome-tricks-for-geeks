---
title: jsDelivr Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/jsdelivr/
---

### `@1-alpha` workaround

When trying to use `@1-alpha` jsDelivr gives an error:

> Couldn't find the requested release version 1-alpha.

**Solution:** Use `@^1.0.0-alpha` instead. This semantic version range will match any `1.x.x` version including alpha releases, effectively targeting the latest `@1` alpha version.

### Purge cache

Purge the cache of a `@latest`, `@alpha` or similar tags to force your users to get the new updated version. Otherwise they might wait up to 7 days:

https://www.jsdelivr.com/tools/purge

Or manually replace:

<pre><code>https://<big>cdn</big>.jsdelivr.net/...
         ↓
https://<big>purge</big>.jsdelivr.net/...
</code></pre>

and hit the resulted link in the browser / [curl](/tricks/terminal/).
