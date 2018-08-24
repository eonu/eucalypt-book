---
description: Destroys a blog article.
---

# Destroy

### Command

```ruby
$ eucalypt blog article destroy
# Alias/shortened
$ eucalypt b article destroy
$ eucalypt b article d
$ eucalypt b a destroy
$ eucalypt b a d
```

### Arguments

* `[URLTITLE]` - The URL title of the article 
  * If argument is empty, then all blog articles will be listed for the user to select one from, and delete.
  * If multiple articles have the same URL title, then all blog articles with that URL title will be listed for the user to select one from, and delete.

### Examples

* `$ eucalypt b article destroy`

  Lists all blog articles for the user to select one from, and delete.

* `$ eucalypt b article destroy my-first-blog-post`

  Deletes a blog article with a URL title of `my-first-blog-post`.

