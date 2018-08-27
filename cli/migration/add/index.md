---
description: Adds an index to a table.
---

# Index

### Command

```ruby
$ eucalypt migration add index
# Alias/shortened
$ eucalypt m add index
$ eucalypt m add i
$ eucalypt m a i
```

### Arguments

* `[TABLE]` - The name of the table.

* `*[COLUMNS]` - The columns to index.

### Options/flags

* `--name` alias `-n`

  The name of the index \(if argument is left empty, ActiveRecord will generate a name for the index\).

* `--options` alias `-o` _\(Possible values: \[unique, length, where, using, type\]\)_

  Additional options for the index.

### Examples

* `$ eucalypt m add index games opening`

  Adds an index on the `opening` column in the `games` table \(with default options\).

* `$ eucalypt m add index games white_elo black_elo`

  Adds a joint index on the `white_elo` and `black_elo` in the `games` table \(with default options\).

* `$ eucalypt m add index games opening -n index_games_on_opening`

  Adds a named index on the `opening` column in the games table.

* `$ eucalypt m add index games opening -o using:gist unique:false`

  Adds a non-unique GIST index on the `opening` column in the `games` table.

