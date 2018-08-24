---
description: Display the metadata of blog articles.
---

# List

### Command

```ruby
$ eucalypt blog article list
# Alias/shortened
$ eucalypt b article list
$ eucalypt b article l
$ eucalypt b a list
$ eucalypt b a l
```

### Options/flags

* `--descending` alias `-d`, _\(Default: True\)_

  Specify whether or not to display blog articles in descending order \(newest first\).

* `--ascending` alias `-a`, _\(Default: False\)_

  Specify whether or not to display blog articles in ascending order \(oldest first\).

* `--tag` alias `-t`

  Search for blog articles by the specified tag \(can be combined with the other search filters\).

* `--year` alias `-Y`

  Search for blog articles by the specified year \(can be combined with the other search filters\).

* `--month` alias `-M`

  Search for blog articles by the specified month \(can be combined with the other search filters\).

* `--day` alias `-D`

  Search for blog articles by the specified day \(can be combined with the other search filters\).

### Examples

* `$ eucalypt b article list -d`

  Display all blog articles in descending order \(newest first\).

* `$ eucalypt b article list -a`

  Display all blog articles in ascending order \(oldest first\).

* `$ eucalypt b article list -t programming`

  Search for blog articles with the `programming` tag.

* `$ eucalypt b article list -Y 2014`

  Search for blog articles written in 2014.

* `$ eucalypt b article list -Y 2016 -D 07`

  Search for blog articles written on the 7th of any month in 2016.

* `$ eucalypt b article list -M 10 -D 31`

  Search for blog articles written on Halloween \(any year\).

* `$ eucalypt b article list -t programming -M 12 -D 25`

  Search for blog articles with the `programming` tag, written on Christmas Day \(sad, I know\).

