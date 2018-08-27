---
description: Creates a table.
---

# Table

### Command

```ruby
$ eucalypt migration create table
# Alias/shortened
$ eucalypt m create table
$ eucalypt m create t
```

### Arguments

* `[NAME]` - The name of the table.

* `*[COLUMN:TYPE]` - The columns/attributes for the database table, along with their types \(argument can be empty\).

### Options/flags

* `--options` alias `-o` _\(Possible values: \[primary\_key, id, temporary, force\]\)_

  Additional options for the table.

### Examples

* `$ eucalypt m create table tweets`

  Generates a new table with default options \(and no columns\).

* `$ eucalypt m create table tweets text:string likes:integer`

  Generates a new table with default options \(and two columns\)

* `$ eucalypt m create table tweets -o temporary:true force:cascade`

  Generates a new table which deletes dependent objects on deletion, and is a temporary table \(and no columns\).

