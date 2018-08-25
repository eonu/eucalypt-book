---
description: Removes a column from a table.
---

# Column

### Command

```ruby
$ eucalypt migration drop column
# Alias/shortened
$ eucalypt m drop column
$ eucalypt m drop c
$ eucalypt m d c
```

### Arguments

* `[TABLE]` - The name of the table.
* `[NAME]` -  The name of the column.

### Example

* \`$ eucalypt m drop column users email\`

  Drops the `email` column from the `users` table.

