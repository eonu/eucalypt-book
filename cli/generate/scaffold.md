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

* `--policy` alias `-p`, _\(Default: False\)_

  Specify whether or not to generate a policy along with the scaffold \(will also add authentication and authorization to the controller if `--rest` option is active\).

* `--headless` alias `-H`, _\(Default: False\)_

  Specify whether the generated policy should be headless \(have no associated model\) \(only works if the `--policy` option is active\).

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

* `$ eucalypt g scaffold tweet -p`

  Generates a new scaffold with a policy.

* `$ eucalypt g scaffold tweet -pH`

  Generates a new scaffold with a headless policy.

* `$ eucalypt g scaffold tweet -rp`

  Generates a new scaffold with a REST-style controller and a policy \(with authenticated and authorized BREAD routes\).

* `$ eucalypt g scaffold tweet -rpH`

  Generates a new scaffold with a REST-style controller and a headless policy \(with authenticated and authorized BREAD routes\).



