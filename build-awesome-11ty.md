---
title: Build Awesome / 11ty Tricks <sub>for Eleventy & Nunjucks</sub>
description: A curated collection of Eleventy (11ty) tricks, starters, command line tips, configuration snippets, and templating techniques.
site: tricks
type: tricks
canonical: https://any.digital/tricks/build-awesome-11ty/
includes:
  - path: _11ty-starters.md
  - text: |-
      ## Command Line & Configuration <small>Tricks</small>

      ### Find and kill <small>11ty processes</small>

      ```sh
      ps aux | grep eleventy
      pkill -f eleventy
      ```

      You can even combine it with other processes hanging around:

      ```sh
      ps aux | grep -E 'eleventy|tailwind|.bin/serve'
      pkill -f tailwind
      pkill -f .bin/serve
      ```
  - #
    # path: ../node_modules/@anydigital/eleventy-blades/src/do/README.md
    path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/do/README.md
  - #
    # path: ../node_modules/@anydigital/eleventy-blades/src/eleventy.config.js
    path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/eleventy.config.js
    section: docs,code
  - text: "## Data & Processing <small>Tricks</small>"
  - #
    # path: ../node_modules/@anydigital/eleventy-blades/src/siteData.js
    path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/siteData.js
    section: docs,code
  - #
    # path: ../node_modules/@anydigital/eleventy-blades/src/processors/markdown.js
    path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/processors/markdown.js
    section: docs,code
  - #
    # path: ../node_modules/@anydigital/eleventy-blades/src/processors/autoLinkFavicons.js
    path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/processors/autoLinkFavicons.js
    section: docs,code
  - path: _njk.md
  - text: |-
      ## Filters
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/attr_concat.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/attr_includes.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/attr_set.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/fetch.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/if.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/merge.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/remove_tag.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/section.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/strip_tag.js
    section: docs,code
  - path: https://raw.githubusercontent.com/anydigital/eleventy-blades/refs/heads/main/src/filters/unindent.js
    section: docs,code
  - text: |-
      ## ![](https://awesome.re/badge.svg)&nbsp; 11ty / Build Awesome <small>[<i>↗</i>](https://github.com/anydigital/awesome-11ty-build-awesome)</small> {#awesome}
  - path: https://raw.githubusercontent.com/anydigital/awesome-11ty-build-awesome/refs/heads/master/README.md
    section: content
  - text: |-
      <small><i class="fa-solid fa-circle-info"></i> This page follows a similar structure to https://www.11ty.dev/docs/projects/</small>

      Featured by:
      - https://11tybundle.dev/blog/11ty-bundle-83/
      - https://11tybundle.dev/categories/nunjucks-macros/
      - https://11tybundle.dev/categories/getting-started/
      - https://github.com/anydigital/awesome-11ty-build-awesome
revised: 2026-02-28
---
