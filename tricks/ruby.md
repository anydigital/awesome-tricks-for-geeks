---
title: Ruby Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/ruby/
---

## Install Ruby projects locally on macOS w/o breaking system's Ruby

### Install `rbenv`

Assuming you already have Homebrew:

```sh
brew install rbenv

# Then list available Ruby versions, and install one:
rbenv install -l
rbenv install 3.2.10

# Set it for current project/folder:
rbenv local 3.2.10
```

Finally, add it to your shell's configuration file so it executes automatically:

``` {data-caption=~/.zshrc}
eval "$(rbenv init -)"
```

### GitHub Pages' Jekyll locally

Assuming you already have `rbenv`:

1. ```rb {data-caption=Gemfile}
   source "https://rubygems.org"

   gem "github-pages", group: :jekyll_plugins
   ```
2. ```sh
   bundle install
   bundle exec jekyll serve
   ```

More info: https://github.com/github/pages-gem#usage, https://jekyllrb.com/docs/installation/macos/

### Slate Docs locally

Assuming you already have `rbenv`:

```sh
bundle install
bundle exec middleman build
```

> For the official version of Slate (v2.13.1), the best and most stable Ruby version is Ruby 3.1.
> While older documentation mentions Ruby 2.6 or 2.7, Slate officially dropped support for Ruby 2.5 and added formal support for Ruby 3.1 in its 2022 releases. Newer versions of Ruby (3.2+) can sometimes cause dependency conflicts with Slate's core engine, middleman, specifically regarding the nokogiri gem.

More info: https://github.com/slatedocs/slate/wiki/Using-Slate-Natively#installing-dependencies-on-macos
