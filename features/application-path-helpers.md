# Application path helpers

### Configuring the root directory

The application root directory is defined as the directory containing the [core application file](core-application-file.md).

You can see its definition in the core application file:

{% code-tabs %}
{% code-tabs-item title="app.rb" %}
```ruby
Eucalypt.set_root __dir__
```
{% endcode-tabs-item %}
{% endcode-tabs %}

There shouldn't be a need to change this, but feel free if it is necessary for your application.

The `set_root` command also generates four helpers.

#### Root accessor

`Eucalypt.root` simply returns the full application root directory path as a string.

#### Path constructor

`Eucalypt.path` allows for the construction of absolute paths relative to the application root directory. 

For example:

```ruby
Eucalypt.path('spec', 'spec_helper.rb')
#=> /Users/eonu/ruby/web/apps/my-app/spec/spec_helper.rb
```

#### Glob helper

`Eucalypt.glob` allows for the globbing of files relative to the application root directory. The method works in the same way as `Dir.glob`, and also accepts a block that allows you to operate on the globbed files. 

For example:

```ruby
Eucalypt.glob('app', 'controllers', '*.rb') do |file|
    file_name = File.basename file, '.rb'
    controller_name = file_name.sub /_controller\Z/, ''
    puts controller_name
end
```

#### Require helper

`Eucalypt.require` allows for the requiring of multiple files relative to the application root directory. Note that it is **not** possible to specify the order in which files are required.

For example:

```ruby
Eucalypt.require 'spec', 'spec_helper'
Eucalypt.require 'spec', 'support', '**', '*.rb'
```

