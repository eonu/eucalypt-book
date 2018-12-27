# Rendering static webpages

### Dynamic webpages

The `erb` method is typically used to render dynamic webpages \(which should be placed in the `app/views` directory\):

```ruby
get '/404' do
  erb :not_found, layout: false
  # Searches for app/views/not_found.erb
end
```

### Static webpages

However, static \(HTML\) webpages can also be rendered in a similar way to dynamic webpages, using the `static` method:

```ruby
get '/' do  
  static '/not_found.html'
  # Searches for app/static/not_found.html
end
```

The `static` method is essentially an alias for Sinatra's `redirect` method.

#### Storage of static files

Static webpages should be stored in the `app/static` directory.

This directory is also shared with any `JSON`, `YAML` or `XML` files that you wish to use within your application - [read here for more information on how to use the data stored in these files](static-data.md).

