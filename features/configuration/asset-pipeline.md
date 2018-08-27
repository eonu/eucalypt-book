# Asset pipeline

### Location

The asset pipeline constitutes the `app/assets` directory.

The configuration file can be found at `config/asset_pipeline.rb`.

### Description

The asset pipeline creates an organized structure for any static assets used in your application. Additionally, it makes it more simple to access these assets.

### Directories

By default, the `assets` sub-directories: `stylesheets`, `scripts`, `images` and `fonts` are included in the asset pipeline.

If [setting up a blog environment](../../cli/blog/setup.md) for your application, then the `blog` sub-directory is also included in the asset pipeline.

You can add a new directory by changing the configuration file.

### Stylesheets

The `stylesheets` sub-directory of the asset pipeline contains all of the stylesheets of the application.

* The template comes with a `partials` folder within this sub-directory that should contain all of the partial stylesheets used in your application.

  Examples of styling that should be in partial stylesheets are colors, breakpoints, mix-ins and fonts \(these partials are already included in Simplatra\).

  ​

  **NOTE**: Stylesheet partials follow the same convention as view partials - that is, file names should be preceded by an underscore. e.g. `_breakpoints.scss`

  ​

* The template also comes with a `__partials__.scss` file, which simply acts as a single file that imports all of the partial files. This makes it easier to include all of the partials into a stylesheet by doing the following, rather than including each partial individually:

{% code-tabs %}
{% code-tabs-item title="app/assets/pages.scss" %}
```css
@import '__partials__';
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Compressors {#compressors}

The default stylesheet compressor is `scss` and the default script compressor/minifier is `uglify`.

These can be changed in the configuration file.

