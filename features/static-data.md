---
description: Accessing and storing static YAML and JSON data.
---

# Static data

### Disambiguation

This documentation page is not about serving static assets. Additionally, the `static` directory is not intended to be used for serving static assets \(other than YAML or JSON files\).

For that purpose, view the [asset pipeline](asset-pipeline.md) documentation page.

### Description

The `static` directory should contain structured data in the YAML or JSON formats.

> Currently supported extensions are: `.yaml`, `.yml`, `.json` and `.geojson`.

The `Static` helper constant can be accessed from anywhere within your application. This constant acts as a link to the `static` directory, allowing you to access data.

### Examples

* The data in a `.geojson` file at `static/server-locations.geojson` can be accessed with:

  ```ruby
  Static.server_locations
  ```

  **NOTE**: The file name is automatically inflected to create a valid Ruby method name. This may lead to differences between the file name and method name as seen in this example \(with the `-` being changed to a `_`\).

* The data in a `.json` file at `static/dependencies/config.json` can be accessed with:

  ```ruby
  Static.dependencies.config
  ```

  **NOTE**: Directory names are also inflected in the same way as file names.

* The data in a `.yml` file at `static/locales.en.yml` can be accessed with:

  ```ruby
  Static.locales.en
  ```

### Viewing defined sub-directory and file methods

The `Object#methods` method can be used to check for defined sub-directory and file methods for the `Static` helper object.

Consider the following directory structure:

```text
static
├── hobbies
│   ├── academic
│   │   └── ruby.yml
│   └── non-academic
│       ├── games
│       │   └── chess.yml
│       └── sports
│           ├── climbing.json
│           └── golf.yml
└── main.yml
```

```ruby
Static.methods(false) #=> [:hobbies, :main]
Static.hobbies.methods(false) #=> [:academic, :non_academic]
Static.hobbies.academic.methods(false) #=> [:ruby]
Static.hobbies.non_academic.methods(false) #=> [:games, :sports]
Static.hobbies.non_academic.games.methods(false)  #=> [:chess]
Static.hobbies.non_academic.sports.methods(false) #=> [:climbing, :golf]
```

### Symbolizing

Data that is read from the files in the `static` directory is automatically converted into a hash.

Since it is Ruby convention that hash keys are symbols, all hash keys accessed through this helper will be symbolized by default \(this can be changed in the [core application file](core-application-file.md), however\).

#### Examples

Consider the following `.yml` file:

{% code-tabs %}
{% code-tabs-item title="app/static/ruby.yml" %}
```yaml
projects:
  frameworks:
    - name: 'Rails'
      repo: 'https://github.com/rails/rails'
    - name: 'Eucalypt'
      repo: 'https://github.com/eucalypt-framework/eucalypt'
```
{% endcode-tabs-item %}
{% endcode-tabs %}

If configured to symbolize the generated hash, then the data for the `Rails` framework can be accessed with:

```ruby
Static.ruby[:projects][:frameworks].first
#=> {:name=>"Rails", :repo=>"https://github.com/rails/rails"}
```

If configured to **not** symbolize the generated hash, then the data for the `Eucalypt` framework can be accessed with:

```ruby
Static.ruby["projects"]["frameworks"].last
#=> {"name"=>"Rails", "repo"=>"https://github.com/eucalypt-framework/eucalypt"}
```



