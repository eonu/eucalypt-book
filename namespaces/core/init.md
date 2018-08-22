---
description: Initialize a new Eucalypt application.
---

# Init

### Command

```text
$ eucalypt init
```

### Arguments

* `[NAME]` - The name of the new Eucalypt application \(note that this is simply a directory name and **cannot** be a path such as `apps/my-new-app`\).

### Options/flags

* `--git`, `--no-git`, _\(Default: True\)_

  Specify whether or not to run `git init` \(to initialize a Git repository\) inside the new application directory.

  \_\_

* `--bundle`, `--no-bundle`, _\(Default: True\)_

  Specify whether or not to run `bundle install` \(to install dependencies\) inside the new application directory.

  \_\_

* `--silence` alias `-s`, _\(Default: False\)_

  Specify whether or not to silence the output of the `git init` and `bundle install` commands \(only silences if either the `--git` or `--no-git` options are active\)

* `--blog` alias `-b`, _\(Default: False\)_

  Specify whether or not to set up the blog environment after initializing the application.

  \_\_

* `--route` alias `-r`, _\(Default: "blog"\)_

  Specify the route of the blog controller \(only works if the `--blog` option is active\).

* `--warden` alias `-w`, _\(Default: False\)_

  Specify whether or not to set up Warden authentication after initializing the application.

* `--pundit` alias `-p`, _\(Default: False\)_

  Specify whether or not to set up Pundit authorization after initializing the application \(only works if the `--warden` option is active\).

### Examples



