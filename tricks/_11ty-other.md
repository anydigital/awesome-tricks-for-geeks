## Find and Kill <small>11ty Processes</small>

```sh
ps aux | grep eleventy
pkill -f eleventy
```

You can even combine with other processes hanging around:

```sh
ps aux | grep -E 'eleventy|tailwind|.bin/serve'
pkill -f tailwind
pkill -f .bin/serve
```

## Awesome 11ty <small>List ![](https://awesome.re/badge.svg)</small>

- https://11tybundle.dev/
- https://github.com/anydigital/sveleven starter
- https://github.com/anydigital/eleventy-bricks utilities
- https://github.com/uncenter/eleventy-plugin-toc
- https://github.com/11ty/eleventy-fetch
- https://sveltiacms.app/en/docs/frameworks/eleventy CMS
