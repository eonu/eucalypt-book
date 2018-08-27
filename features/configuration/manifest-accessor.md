# Manifest accessor

### Location

The manifest accessor method is in the file is located at `app/config/manifest.rb`.

### Usage {#usage}

* To include the manifest stylesheet file `application.css` in a view file:

  ```markup
  <html>
      <head><%= application :css %></head>
      <body></body>
  </html>
  ```

* To include the manifest javascript file `application.js` in a view file:

  ```markup
  <html>
      <head><%= application :js %></head>
      <body></body>
  </html>
  ```

* To include both the manifest javascript and stylesheet files in a view file:

  ```markup
  <html>
      <head><%= application :css, :js %></head>
      <body></body>
  </html>
  ```

