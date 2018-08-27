---
description: Renames a table.
---

# Table

### Command

```ruby
$ eucalypt migration rename table
# Alias/shortened
$ eucalypt m rename table
$ eucalypt m rename t
$ eucalypt m r t
```

### Arguments

* `[OLD]` - The name of the table to change.

* `[NEW]` - The new name of the table.

### Examples

* `$ eucalypt m rename table usesr users`

  Renames the incorrectly spelled `usesr` table to `users`.

