---
description: Runs all application specs.
---

# Test

### Commands

```bash
$ eucalypt test
# Alias/shortened
$ eucalypt t
```

### Options/flags

* `--summarized` alias `-s`, _\(Default: False\)_

  Runs RSpec in summarized report form \(`rspec -fd spec`\).

### Examples

* `$ eucalypt test`

  Runs all application specs with default options.

* `$ eucalypt test -s`

  Runs all application specs, displaying results in a summarized report form.

