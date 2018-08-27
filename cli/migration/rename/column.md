---
description: Renames a column.
---

# Column

### Command

```ruby
$ eucalypt migration rename column
# Alias/shortened
$ eucalypt m rename column
$ eucalypt m rename c
$ eucalypt m r c
```

### Arguments

* `[TABLE]` - The name of the table.

* `[OLD]` - The name of the column to change.

* `[NEW]` - The new name of the column.

### Examples

* `$ eucalypt m rename column users emali email`

  Renames the incorrectly spelled `emali` column to `email` on the `users` table.

