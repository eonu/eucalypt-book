# Views

### Location {#location}

The view files are located in the `app/views` directory.

### Rendering

Eucalypt looks for view files relative to the `app/views` directory by default \(though you can change this in the [core application file](../core-application-file.md)\).

#### Views directly inside directory {#views-directly-inside-directory}

If your `views` folder structure is like the following:

```text
views
├── partials
├── layouts
├── index.erb
└── 404.erb
```

Then you can render the pages `index.erb` and `404.erb` in the following way:

{% code-tabs %}
{% code-tabs-item title="app/controllers/application\_controller.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  helpers ApplicationHelper if defined? ApplicationHeler
  
  get '/' do
    erb :index
  end
  
  error Sinatra::NotFound do
    erb :"404"
  end 
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Views inside sub-directories

If your `views` folder structure is like the following \(with some views located within sub-directories\):

```text
views
├── partials
├── layouts
├── pages
│   ├── index.erb
│   └── about.erb
└── 404.erb
```

Then you can render the pages `index.erb` and `404.erb` in the following way \(note the specification of the full path relative to `app/views` for rendering the `index` page\):

{% code-tabs %}
{% code-tabs-item title="app/controllers/application\_controller.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  helpers ApplicationHelper if defined? ApplicationHeler
  
  get '/' do
    erb :"pages/index"
  end
  
  error Sinatra::NotFound do
    erb :"404"
  end 
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

