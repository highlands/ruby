# RuboCop Church of the Highlands

Church of the Highlands specific analysis for [RuboCop](https://github.com/rubocop-hq/rubocop).

It contains Church of the Highlands' internally used configuration for
[RuboCop](https://github.com/rubocop-hq/rubocop) and
[RuboCop RSpec](https://github.com/backus/rubocop-rspec). It also includes a handful custom rules
that are not currently addressed by other projects.

## Installation

Just put this in your `Gemfile` it depends on the appropriate version of rubocop and rubocop-rspec.

```
gem 'rubocop-highlands'
```

## Usage

You need to tell RuboCop to load the Highlands extension. There are three
ways to do this:

### RuboCop configuration file
First Create a new file `.rubocop_highlands.yml` in the same directory as your `.rubocop.yml`
this file should contain
```
require:
  - rubocop-highlands
```

Next add the following to `.rubocop.yml`
or add before `.rubocop_todo.yml` in your existing `inherit_from`

```
inherit_from:
  - .rubocop_highlands.yml
  - .rubocop_todo.yml
```

You need to inherit `.rubocop_highlands.yml` from another file because of Rubocop order of operations.
It runs `inherit_from` before `require` commands. If the configuration is not in a separate file
you could potentially experience a bunch of warnings from `.rubocop_todo.yml` for non-existant
`Highlands` rules.

Now you can run `rubocop` and it will automatically load the RuboCop Highlands
cops together with the standard cops.

### Command line

```bash
rubocop --require rubocop-highlands
```

## The Cops

All cops are located under
[`lib/rubocop/cop/highlands`](lib/rubocop/cop/highlands), and contain
examples/documentation.

In your `.rubocop.yml`, you may treat the Church of the Highlands cops just like any other
cop. For example:

```yaml
Highlands/PhraseBundleKeys:
  Exclude:
    - spec/my_poorly_named_spec_file.rb
```

