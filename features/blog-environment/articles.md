# Articles

### CLI tasks

* [Article](../../cli/blog/article/)

### Frontmatter

`YAML` front matter acts as the metadata for your markdown articles. It tells Eucalypt all of the important information about your post. Front matter is located at the top of a markdown file, and is the `YAML` code located between the two pairs of `---` separators.

The actual content of your article should go after the front matter.

For the article created by the command in the previous section, its markdown article file would look like this:

```yaml
---
title: "TODO"
desc: "TODO"
tags: ["TODO"]
# Only change the below fields with `eucalypt blog article edit` commands!
urltitle: "first-article"
time: "2018-06-06 00:00:01"
assetpath: "/assets/2018/06/06/first-article"
---
```

As the warning says, you should **avoid** changing the values of `urltitle`, `time` or `assetpath`, as it will require you to change the directory structure of you application \(particularly the view and asset directories\), as well as any other reference you made to the images of this article and the post itself. 

The `eucalypt blog article edit` commands will automatically do this for you.

However, feel free to change the `title`, `desc` and `tags` fields in the markdown file.

* `title` - Title of your article
* `desc` - Description of your article
* `tags` - Tags indicating the topics of the article. Should be single or hyphenated words
  * e.g. `ruby`, `meta-programming`, `web-dev`, `sinatra`

#### Asset path {#asset-path}

The purpose of `assetpath` in the `YAML` front matter is to show the user where to access the assets for the article.

Whenever you need to include an asset, simply copy this asset path and append the asset file to the end of the file path.

For more information as to why the asset path URL looks like this, read the [asset pipeline page](../configuration/asset-pipeline/).

**Example**: If you wanted to include `header.png` in the article \(after placing the image in the correct place `app/assets/blog/2018/06/06/first-article/header.png`\):

```yaml
---
title: "TODO"
desc: "TODO"
tags: ["TODO"]
# Only change the below fields with `simplatra blog article edit` commands!
urltitle: "first-article"
time: "2018-06-06 00:00:01"
assetpath: "/assets/2018/06/06/first-article"
---
​
![Header](/assets/2018/06/06/first-article/header.png)
```

