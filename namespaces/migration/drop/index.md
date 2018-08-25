---
description: Removes an index from a table.
---

# Index

### Command

```ruby
$ eucalypt migration drop index
# Alias/shortened
$ eucalypt m drop index
$ eucalypt m drop i
$ eucalypt m d i
```

### Arguments

* `[TABLE]` - The name of the table.

* `*[COLUMNS]` - The columns of the table that the index should be removed from.

### Options/flags

* `--name` alias `-n`

  The name of the index to remove \(if this flag is active, the `*[COLUMNS]` argument should be empty\).

### Example

* `$ eucalypt m drop index games opening`

  Removes the index on the `opening` column of the `games` table.

* `$ eucalypt m drop index games white_elo black_elo`

  Removes the joint index on the `white_elo` and `black_elo` columns of the `games` table.

* `$ eucalypt m drop index games -n index_games_on_opening`

  Removes the `index_games_on_opening` index on the `games` table.

