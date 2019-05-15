---
description: Launches an interactive console with all application files loaded.
---

# Console

### Command

```bash
$ eucalypt console
# Alias/shortened
$ eucalypt c
```

### Arguments

* `[ENV]` - The environment to run the console on. This can be one of:

  * `production` alias `p`
  * `development` alias `d` 
  * `test` alias `t`

  Defaults to the value of the `APP_ENV` environment variable. If this is not set, then the default environment is `development`.

### Examples

* `$ eucalypt console`

  Runs the console in the default environment.

* `$ eucalypt console production`

  Runs the console in the production environment.

