# Manifest accessor

### Usage

* To include the manifest stylesheet file `application.css` in a view file:

  ```markup
  <html>
      <head><%= manifest :stylesheet %></head>
      <body></body>
  </html>
  ```

* To include the manifest javascript file `application.js` in a view file:

  ```markup
  <html>
      <head><%= manifest :script %></head>
      <body></body>
  </html>
  ```

* To include both the manifest javascript and stylesheet files in a view file:

  ```markup
  <html>
      <head><%= manifest :stylesheet, :script %></head>
      <body></body>
  </html>
  ```

