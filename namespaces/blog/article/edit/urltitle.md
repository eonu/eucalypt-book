---
description: Edit the URL title of a blog article.
---

# Urltitle

### Command

```ruby
$ eucalypt blog article edit urltitle
# Alias/shortened
$ eucalypt b article edit urltitle
$ eucalypt b article edit u
# etc ...
$ eucalypt b a e u
```

### Arguments

* `[URLTITLE]` - The URL title of the article.
  * If argument is empty, then all blog articles will be listed for the user to select one from, and edit.
  * If multiple articles have the same URL title, then all blog articles with that URL title will be listed for the user to select one from, and edit.

### Examples

* `$ eucalypt b article edit urltitle`

  Lists all blog articles for the user to select one from, and edit.

* `$ eucalypt b article edit urltitle my-first-blog-post`

  Edits a blog article with a URL title of `my-first-blog-post`.

