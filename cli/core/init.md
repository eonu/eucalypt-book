---
description: Initialize a new application.
---

# Init

### Command

```bash
$ eucalypt init
# Alias/shortened
$ eucalypt i
```

### Arguments

* `[NAME]` - The name of the new application \(note that this is simply a directory name and **cannot** be a path such as `apps/my-new-app`\).

### Options/flags

* `--git`, `--no-git`, _\(Default: True\)_

  Specify whether or not to run `git init` \(to initialize a Git repository\) inside the new application directory.

  \_\_

* `--bundle`, `--no-bundle`, _\(Default: True\)_

  Specify whether or not to run `bundle install` \(to install dependencies\) inside the new application directory.

  \_\_

* `--silence` alias `-s`, _\(Default: False\)_

  Specify whether or not to silence the output of the `git init` and `bundle install` commands \(only silences if either the `--git` or `--bundle` options are active\)

* `--blog` alias `-b`, _\(Default: False\)_

  Specify whether or not to set up the blog environment after initializing the application.

  \_\_

* `--route` alias `-r`, _\(Default: "blog"\)_

  Specify the route of the blog controller \(only works if the `--blog` option is active\).

### Examples

* `$ eucalypt init my-new-app` 

  Generates a new application with default options.

* `$ eucalypt init my-new-app -s`

  Generates a new application and silences the `bundle install` and `git init` commands.

* `$ eucalypt init my-new-app --no-bundle --no-git` 

  Generates a new application and skips dependency installation \(`bundle install`\) and Git repository initialization \(`git init`\).

* `$ eucalypt init my-new-app -b` 

  Generates a new application and runs blog environment setup.

* `$ eucalypt init my-new-app -br posts` 

  Generates a new application and runs blog environment setup at `/posts`.

