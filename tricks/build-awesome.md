---
title: Build Awesome Tricks <sub>for Eleventy (11ty) & Nunjucks</sub>
description: A curated collection of Eleventy (11ty) tricks, starters, command line tips, configuration snippets, and templating techniques.
site: tricks
type: tricks
canonical: https://any.digital/tricks/build-awesome/
includes:
  - path: tricks/_11ty-starters.md
  - text: |-
      ## Command Line <small>Tricks</small>

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
    path: https://raw.githubusercontent.com/anydigital/eleventy-bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/eleventy-bricks/README.md
    section: npm-h3
  - text: "## Configuration <small>Tricks</small>"
  - #
    path: https://raw.githubusercontent.com/anydigital/eleventy-bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/eleventy-bricks/README.md
    section: config-h3
  - text: "## Data & Processing <small>Tricks</small>"
  - #
    path: https://raw.githubusercontent.com/anydigital/eleventy-bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/eleventy-bricks/README.md
    section: data&processors-h3
  - path: tricks/_njk.md
  - #
    path: https://raw.githubusercontent.com/anydigital/bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/bricks/README.md
    section: njk-liquid-h2
  - #
    path: https://raw.githubusercontent.com/anydigital/eleventy-bricks/refs/heads/main/README.md
    # path: ../node_modules/@anydigital/eleventy-bricks/README.md
    section: filters-h2
  - text: |-
      ## [Awesome Build Awesome](https://github.com/anydigital/awesome-build-awesome) <sub>![](https://awesome.re/badge.svg)</sub> {#awesome}

      - https://github.com/anydigital/eleventy-bricks utilities
      - https://github.com/uncenter/eleventy-plugin-toc
      - https://github.com/11ty/eleventy-fetch
      - https://any.digital/tricks/11ty/
      - https://any.digital/tricks/njk-liquid/ templating
      - https://eleventy-explorer.netlify.app/ for more
      - https://any.digital/insights/ssg/
  - path: https://raw.githubusercontent.com/anydigital/eleventy-build-awesome/refs/heads/master/README.md
    section: content
  - text: |-
      <small>This page follows a similar structure to https://www.11ty.dev/docs/projects/</small>

      Featured in:
      - https://11tybundle.dev/blog/11ty-bundle-83/
      - https://11tybundle.dev/categories/nunjucks-macros/
      - https://11tybundle.dev/categories/getting-started/
      - https://github.com/anydigital/eleventy-build-awesome
revised: 2026-02-28
---
