# IP whitelisting

If there are certain routes or views which you would like to IP-protect within your application, the `Eucalypt::Whitelist` class provides a simple way to do this.

### Configuration

By default, the `:whitelist` setting is set to:

{% code-tabs %}
{% code-tabs-item title="app.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  .
  .
  # Set IP whitelist
  set :whitelist, Eucalypt::Whitelist.new(Eucalypt.path 'config', 'whitelist')
  .
  .
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This allows hashed whitelisted IP addresses to be stored in the `config/whitelist` file \(no extension\).

#### Disabling whitelisting

To disable whitelisting, IP checks and IP protection, simply remove the `set` statement explained above, and disable the `:whitelist` setting:

{% code-tabs %}
{% code-tabs-item title="app.rb" %}
```ruby
class ApplicationController < Sinatra::Base
  .
  .
  # Set IP whitelist
  disable :whitelist
  .
  .
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Whitelist file

Each line in the `config/whitelist` file represents a hashed IP address.

By default, the IP addresses `::1`, `0.0.0.0` and `127.0.0.1` are added to the whitelist.

**There should be no need to modify this file manually** - all modifications should be done through use of the `whitelist` helper method \(which is a reference to the `Eucalypt::Whitelist` instance that was defined in the `:whitelist` setting\).

For example in the `eucalypt console`, we can add and remove IP addresses to the whitelist file, as well as checking whether an IP address is whitelisted:

```ruby
irb(main):001:0> app.whitelist.add '40.138.232.44', '62.215.74.904'
irb(main):002:0> app.whitelist.remove '62.215.74.904'
irb(main):003:0> app.whitelist.include? '40.138.232.44'
#=> true
irb(main):004:0> app.whitelist.include? '62.215.74.904'
#=> false
```

### Helper methods

* `whitelisted?` - This helper method can be used in route definitions and dynamic views. It returns `true` or `false` depending on whether the current requesting IP address \(`request.ip`\) is whitelisted. For example:



  ```markup
  <div>
      <p><b>This login form is IP-protected</b></p>
      <form>
          ...
          <% if whitelisted? %>
          <button type="button">Login</button>
          <% else %>
          <p>Your IP address is not whitelisted!</p>
          <% end %>
  	</form>
  </div>
  ```

* `ip_check` - This helper method should be used in route definitions, to only allow certain actions to be performed if the requesting IP address is whitelisted. This method raises a `Eucalypt::NotWhitelistedError`, which you can handle how you like. For example:



  ```ruby
  class AuthenticationController < ApplicationController(route: '/login')
    get '/' do
      erb :login, locals: {flash: flash}
    end
    
    post '/' do
      ip_check
      # Perform login stuff here
    rescue Eucalypt::NotWhitelistedError
      flash[:unwhitelisted] = "Unable to log in - your IP address is not whitelisted"
      redirect to '/'
    end
  end
  ```

