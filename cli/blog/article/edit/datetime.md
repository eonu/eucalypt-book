---
description: Edit the datetime of a blog article.
---

# Datetime

### Command

```ruby
$ eucalypt blog article edit datetime
# Alias/shortened
$ eucalypt b article edit datetime
$ eucalypt b article edit d
# etc ...
$ eucalypt b a e d
```

### Arguments

* `[URLTITLE]` - The URL title of the article.
  * If argument is empty, then all blog articles will be listed for the user to select one from, and edit.
  * If multiple articles have the same URL title, then all blog articles with that URL title will be listed for the user to select one from, and edit.

### Examples

* `$ eucalypt b article edit datetime`

  Lists all blog articles for the user to select one from, and edit.

* `$ eucalypt b article edit datetime my-first-blog-post`

  Edits a blog article with a URL title of `my-first-blog-post`.

