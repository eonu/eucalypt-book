---
description: Sets up Warden authentication.
---

# Setup

### Command

```ruby
$ eucalypt security warden setup
# Alias/shortened
$ eucalypt s warden setup
$ eucalypt s warden s
$ eucalypt s w s
```

### Options/flags

* `--controller`, `--no-controller`, _\(Default: True\)_

  Specify whether or not to generate an authentication controller.

### Examples

* `$ eucalypt s warden setup`

  Sets up Warden authentication with default options.

* `$ eucalypt s warden setup --no-controller`

  Sets up Warden authentication \(without an authentication controller\).

