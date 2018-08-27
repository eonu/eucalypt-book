---
description: Create a new Pundit policy.
---

# Generate

### Command

```ruby
$ eucalypt security policy generate
# Alias/shortened
$ eucalypt s policy generate
$ eucalypt s policy g
```

### Arguments

* `[NAME]` - The name of the policy.

### Options/flags

* `--headless` alias `-H`, _\(Default: False\)_

  Specify whether or not to generate a headless policy \(a policy which does not have a corresponding model\).

* `--permissions` alias `-p`

  Permissions to generate along with the policy.

### Examples

* `$ eucalypt s policy g product`

  Generate a `product` policy with default options.

* `$ eucalypt s policy g post -H`

  Generate a headless `post` policy.

* `$ eucalypt s policy g product -p add edit delete`

  Generate a `product` policy with permissions to `add`, `edit` and `delete`.

* `$ eucalypt s policy g post -Hp add edit delete`

  Generate a headless `post` policy with permissions to `create`, `edit` and `delete`.

