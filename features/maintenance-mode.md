# Maintenance mode

If you wish to disable access to all routes of your application and redirect every requested route to a certain route, this can be done with a `maintenance` route.

This can be configured in `app.rb`:

{% code-tabs %}
{% code-tabs-item title="app.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  .
  # Set maintenance route
  maintenance enabled: true do
    erb :maintenance, layout: false
  end
  .
  .
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This action is typically [rendering a static webpage](rendering-static-webpages.md) that details the reasons for maintenance:

```ruby
class ApplicationController < Sinatra::Base
  .
  # Set maintenance route
  maintenance enabled: true do
    render_static '/maintenance.html'
  end
  .
  .
end
```

Note that `maintenance` simply is just a `get` route, so some sort of rendering, redirecting, or other valid return must be done.

