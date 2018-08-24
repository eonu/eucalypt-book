---
description: Sets up the blog environment.
---

# Setup

### Command

```ruby
$ eucalypt blog setup
# Alias/shortened
$ eucalypt b setup
$ eucalypt b s
```

### Options/flags

* `--route` alias `-r` _\(Default: "blog"\)_

  The route at which the blog controller serves the blog.

  E.g. `posts` would route the blog to `/posts`.

### Examples

* `$ eucalypt blog setup`

  Sets up the blog environment at the default route `/blog`.

* `$ eucalypt blog setup -r posts`

  Sets up the blog environment at the route `/posts`.

