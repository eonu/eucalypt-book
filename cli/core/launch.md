---
description: Launches your application.
---

# Launch

### Command

```bash
$ eucalypt launch
# Alias/shortened
$ eucalypt l
```

### Arguments

* `[ENV]` - The environment to serve the application on. This can be one of:

  * `production` alias `p`
  * `development` alias `d` 
  * `test` alias `t`

  Defaults to the value of the `APP_ENV` environment variable. If this is not set, then the default environment is `development`.

### Options/flags

* `--port` alias `-p`_\(Default: 9292\)_

  Specify which port to serve the application on.

* `--rerun` alias `-r` _\(Default: False\)_

  Specify whether or not to use the `rerun` gem to watch the application files and automatically restart the server when any changes are detected.

* `--quiet` alias `-q` _\(Default: False\)_

  Specify whether or not to silence the output of `rerun` \(only works if the `--rerun` option is active\).

### Examples

* `$ eucalypt launch`

  Launches your application with default options and default environment.

* `$ eucalypt launch production`

  Launches your application on the production environment with default options.

* `$ eucalypt launch -p 6241`

  Launches your application on port `6241` on the default environment.

* `$ eucalypt launch -r`

  Launches your application with default environment, with automatic server restart when watched files are updated \(with `rerun`\).

* `$ eucalypt launch -rq`

  Launches your application with default environment, with automatic server restart when watched files are updated \(with `rerun`\), but with output silenced.

