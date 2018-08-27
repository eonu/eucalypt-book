---
description: Adds a column to a table.
---

# Column

### Command

```ruby
$ eucalypt migration add column
# Alias/shortened
$ eucalypt m add column
$ eucalypt m add c
$ eucalypt m a c
```

### Arguments

* `[TABLE]` - The name of the table.

* `[COLUMN]` - The name of the column.

* `[TYPE]` - The column type.

### Options/flags

* `--options` alias `-o` _\(Possible values: \[limit, default, null, precision, scale\]\)_

  Additional options for the column.

### Examples

* `$ eucalypt m add column games eco integer`

  Adds an `eco` column to the `games` table, with type `integer` \(with default options\).

* `$ eucalypt m add column games eco integer -o null:false`

  Adds a non-null `eco` column to the `games` table, with type `integer` \(with default options\).

