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
static '/not_found.html'
```

The `static` method basically generates a `get` route for the specified file path. In this example, the file should exist at `app/static/public/not_found.html`.

#### Aliases

Alias routes can be given for static routes:

```ruby
static '/maintenance.html', aliases: %w[/maintenance /busy]
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

