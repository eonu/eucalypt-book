---
description: Changes a column's type definition.
---

# Column

### Command

```ruby
$ eucalypt migration change column
# Alias/shortened
$ eucalypt m change column
$ eucalypt m change c
```

### Arguments

* `[TABLE]` - The name of the table.

* `[COLUMN]` - The name of the column.

* `[TYPE]` - The new type for the column.

### Options/flags

* `--options` alias `-o` _\(Possible values: \[limit, default, null, precision, scale\]\)_

  Additional options for the column.

### Examples

* `$ eucalypt m change column users email string`

  Change the `email` column on the `users` table to a `string` type.

* `$ eucalypt m chance column users email string -o null:false`

  Change the `email` column on the `users` table to a `string` type, and make it non-null.

