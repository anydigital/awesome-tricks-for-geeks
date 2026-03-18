---
permalink: /
site:
  inline_styles: |-
    @media (max-width: 767px) {
      h1 {
        font-size: 1.75em;

        br {
          display: none;
        }
      }
    }
eleventyComputed:
  hero: |-
    {% liquid
      #TODO as trick
      # assign _ = '../node_modules/@anydigital/blades/README.md'
      assign _ = 'https://raw.githubusercontent.com/anydigital/blades/refs/heads/main/README.md'
      echo _ | fetch | section: 'hero' | replace: 'hgroup>', 'h1>' | replace: '<wbr>', '<br>'
    %}
includes:
  - #
    # path: ../node_modules/@anydigital/blades/README.md
    path: https://raw.githubusercontent.com/anydigital/blades/refs/heads/main/README.md
    section: index
---
