# Maintenance mode

If you wish to completely disable access to all routes of your application \(commonly to perform some sort of maintenance\), this can be done by toggling the `:maintenance` setting in `app.rb` \(this is disabled by default\):

{% code-tabs %}
{% code-tabs-item title="app.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  .
  .
  # Toggle maintenance mode
  enable :maintenance
  .
  .
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Maintenance route

A special `maintenance` route can be defined, which tells the application what action to perform when any route is requested while the application is in maintenance mode.

This action is typically [rendering a static webpage](rendering-static-webpages.md) that details the reasons for maintenance:

{% code-tabs %}
{% code-tabs-item title="app/controllers/application\_controller.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  maintenance do
    erb :maintenance, layout: false
  end
    
  get '/' do
    erb :index, layout: false 
  end
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}



Note that `maintenance` simply is just a `get` route \(that redirects all other routes to it\), so some sort of rendering, redirecting, or other valid return must be done.

* **This route must be the first route defined in your entire application, and should therefore be defined at the top of `ApplicationController` in `app/controllers/application_controller.rb`**

  \*\*\*\*

* **This route is only active as long as the `maintenance` setting is enabled.**

