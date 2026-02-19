---
title: Ruby Tricks
site: tricks
type: tricks
canonical: https://any.digital/tricks/ruby/
---

### Install and build Slate Docs locally on macOS w/o breaking system's Ruby

```sh
brew install rbenv
# First, list available Ruby versions:
rbenv install -l
# Then install:
rbenv install 3.2.10
gem install bundler
bundle install
bundle exec middleman build
```

> For the official version of Slate (v2.13.1), the best and most stable Ruby version is Ruby 3.1.
> While older documentation mentions Ruby 2.6 or 2.7, Slate officially dropped support for Ruby 2.5 and added formal support for Ruby 3.1 in its 2022 releases. Newer versions of Ruby (3.2+) can sometimes cause dependency conflicts with Slate's core engine, middleman, specifically regarding the nokogiri gem.

Read more: https://github.com/slatedocs/slate/wiki/Using-Slate-Natively#installing-dependencies-on-macos
