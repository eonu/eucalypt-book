# Rendering static files

### Dynamic webpages

The `erb` method is typically used to render dynamic webpages \(which should be placed in the `app/views` directory\):

```ruby
get '/404' do
  erb :not_found, layout: false
  # Searches for app/views/not_found.erb
end
```

### Static files

However, static files can also be rendered in a similar way to dynamic webpages, using the `render_static` method:

```ruby
get '/404' do
  render_static '/not_found.html'
  # Searches for app/static/public/not_found.html
end
```

Alternatively, the `static` method can be used to define a block. The above can be simplified into:

```ruby
static '/not_found.html', aliases: %w[/404]
```

The `static` method basically generates a `get` route for the specified file path, along with its aliases. Aliases are not required though:

```ruby
static '/not_found.html'
```

#### Block definition

If you wish to define multiple static routes at once, you can use the block format:

```ruby
static do |s|
  s.route '/not_found.html'
  s.route '/maintenance.html', aliases: %w[/maintenance]
  s.route '/robots.txt'
end
```

#### Storage of static files

Static webpages should be stored in the `app/static/public` directory.

If you wish to access the data stored in any `JSON`, `YAML` or `XML` files in this directory \(somewhere within your Ruby code\), use the Static data accessor `Static.public`  - [read here for more information on how to use the data stored in these files](static-data.md).

