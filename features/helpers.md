---
description: Helpers modules contain methods that can be used in controllers and views.
---

# Helpers

### CLI tasks

* [Generate](../cli/generate/helper.md)
* [Destroy](../cli/destroy/helper.md)

### Example

```ruby
module ProductHelper
  def quantity(product)
    String.build do |s|
      s << product.quantity.to_s
      s << " "
      s << product.pluralize(product.quantity, product.name)
      s << " remaining."
    end
  end
  
  def name(product)
    product.name.titleize
  end
end
```

* The `quantity` and `name` helper methods will only be accessible within the `ProductController` class and any views rendered from that class.

### Application helper

The application helper works slightly differently. The application helper is included in the `ApplicationController` class. 

Since `ApplicationController` is inherited from every new controller, **every controller \(and view\) has access to helper methods defined in the application helper**.

Methods should only be defined in this module if you want them accessible from all parts of your application.

