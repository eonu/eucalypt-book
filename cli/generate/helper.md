---
description: Generates a helper.
---

# Helper

### Command

```ruby
$ eucalypt generate helper
# Alias/shortened
$ eucalypt g helper
```

### Arguments

* `[NAME]` - The name of the helper.

### Options/flags

* `--spec`, `--no-spec`, _\(Default: True\)_

  Specify whether or not to generate a spec file along with the helper.

### Examples

* `$ eucalypt g helper tweet`

  Generates a new helper with default options.

* `$ eucalypt g helper tweet --no-spec`

  Generates a new helper without a corresponding spec file.

