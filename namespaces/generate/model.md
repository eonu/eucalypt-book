---
description: Generates a model.
---

# Model

### Command

```ruby
$ eucalypt generate model
# Alias/shortened
$ eucalypt g model
$ eucalypt g m
```

### Arguments

* `[NAME]` - The name of the model.

* `*[COLUMN:TYPE]` - The columns/attributes for the model's database table, along with their types \(argument can be empty\).

### Options/flags

* `--spec`, `--no-spec`, _\(Default: True\)_

  Specify whether or not to generate a spec file along with the model.

* `--table`, `--no-table`, _\(Default: True\)_

  Specify whether or not to generate a table creation migration along with the model.

### Examples

* `$ eucalypt g model tweet`

  Generates a new model with default options \(and no columns\).

* `$ eucalypt g model tweet text:string likes:integer`

  Generates a new model with default options \(and three columns\)

* `$ eucalypt g model tweet text:string likes:integer --no-spec`

  Generates a new model without a corresponding spec file \(and three columns\).

* `$ eucalypt g model tweet --no-table`

  Generates a new model file with a corresponding spec file, but with no table creation migration.

