---
description: Renames an index.
---

# Index

### Command

```ruby
$ eucalypt migration rename index
# Alias/shortened
$ eucalypt m rename index
$ eucalypt m rename i
$ eucalypt m r i
```

### Arguments

* `[TABLE]` - The name of the table.

* `[OLD]` - The name of the index to change.

* `[NEW]` - The new name of the index.

### Examples

* `$ eucalypt m rename index games index_on_openig index_on_opening`

  Renames the incorrectly spelled `index_on_openig` index to `index_on_opening` on the `games` table.

