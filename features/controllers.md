---
description: >-
  Controllers map the application to a specified base route. Each controller
  also contains routes that extend from the base route.
---

# Controllers

### CLI tasks

* [Generate](../cli/generate/controller.md)
* [Destroy](../cli/destroy/controller.md)

### Example

{% code-tabs %}
{% code-tabs-item title="app/controllers/product\_controller.rb" %}
```ruby
class ProductController < Eucalypt::Controller(route: '/products')
  helpers ProductHelper if defined? ProductHelper
  
  # Route: /products/
  get '/' do
    @products = Product.all
    erb :'products/browse'
  end
  
  # Route: /products/:id
  get '/:id' do |id|
    @product = Product.find id
    erb :'products/show'
  end
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* The base route for the controller is specified in line `1`:

  ```ruby
  ... < Eucalypt::Controller(route: '/products')
  ```

* Routes defined within this controller are relative to the base route \(`/products`\). This means that:
  * `get '/'` maps to the route `/products/`
  * `get '/:id'` maps to the route `/products/:id`

### Application controller

The application controller works slightly differently. Since it inherits directly from `Sinatra::Base`, you cannot specify a base route, as the controller is always mounted at `/`.

