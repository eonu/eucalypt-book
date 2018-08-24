---
description: Generates a controller.
---

# Controller

### Command

```ruby
$ eucalypt generate controller
# Alias/shortened
$ eucalypt g controller
$ eucalypt g c
```

### Arguments

* `[NAME]` - The name of the controller.

### Options/flags

* `--spec`, `--no-spec`, _\(Default: True\)_

  Specify whether or not to generate a spec file along with the controller.

  \_\_

* `--rest` alias `-r`, _\(Default: False\)_

  Specify whether or not to generate a REST-style controller, with [BREAD](http://paul-m-jones.com/archives/291) method route handler templates.

### Examples

* `$ eucalypt g controller tweet`

  Generates a new controller with default options.

* `$ eucalypt g controller tweet --no-spec`

  Generates a new controller without a corresponding spec file.

* `$ eucalypt generate controller tweet -r`

  Generates a REST-style controller.

