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

<sup>✅ Discovered by [TfG](/tricks/)</sup>


### Purge cache

Purge the cache of a `@latest`, `@alpha` or similar to force your users to get the new updated version. Otherwise they might wait up to 7 days:

https://www.jsdelivr.com/tools/purge

Or manually by simply replacing <code>https://<big>cdn</big>.jsdelivr.net/...</code> to <code>//<big>purge</big>.</code>
