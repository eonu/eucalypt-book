---
description: Generates a scaffold.
---

# Scaffold

### Command

```ruby
$ eucalypt generate scaffold
# Alias/shortened
$ eucalypt g scaffold
$ eucalypt g s
```

### Arguments

* `[NAME]` - The name of the scaffold.

* `*[COLUMN:TYPE]` - The columns/attributes for the model's database table, along with their types \(argument can be empty\).

### Options/flags

* `--no` alias `-n`, _\(Possible values: \[h, hs, c, cs, m, ms\]\)_

  Specify what files to omit during the generation of the scaffold:

  * `h` - Helper file
  * `hs` - Helper spec file
  * `c` - Controller file
  * `cs` - Controller spec file
  * `m` - Model file
  * `ms` - Model spec file

* `--rest` alias `-r`, _\(Default: False\)_

  Specify whether or not to generate a REST-style controller, with [BREAD](http://paul-m-jones.com/archives/291) method route handler templates.

* `--table`, `--no-table`, _\(Default: True\)_

  Specify whether or not to generate a table creation migration along with the model.

### Examples

* `$ eucalypt g scaffold tweet`

  Generates a new scaffold with default options \(and no columns\).

* `$ eucalypt g scaffold tweet text:string likes:integer`

  Generates a new scaffold with default options \(and two columns\)

* `$ eucalypt g scaffold tweet -n h hs ms cs`

  Generates a new scaffold without a helper, helper spec, model spec or controller spec \(and no columns\).

* `$ eucalypt g scaffold tweet --no-table`

  Generates a new scaffold with no table creation migration.

* `$ eucalypt g scaffold tweet -r`

  Generates a new scaffold with a REST-style controller.



