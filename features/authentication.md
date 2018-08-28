---
description: >-
  Authentication is the process of verifying the identify of a user. It is
  handled by Warden, and comes with a basic setup with helpers for
  authenticating routes.
---

# Authentication

### User model

Once you have [set up authentication](../cli/security/warden/setup.md), you will see that a model was created for storing user's account information. This model is located at `app/models/user.rb`.

The default columns in the model are `username` and `encrypted_password`.

#### Password encryption

For security, passwords are hashed using the BCrypt encryption algorithm. The encryption mechanism is already built into the user model.

When creating a new user, it is essential that the encrypted password is stored in the database, and not the unencrypted one.

#### Creating a new user

To create a new user:

```ruby
user = User.new
user.username = 'admin'
user.password = '123'
user.save
```

Although this appears to be storing the unencrypted password in the database, the `password=` instance method will first encrypt the password.

```ruby
#<User id: 1, username: "admin", encrypted_password: "$2a$10$pnS4ALhE2X5VUu1GuGrS2.c1Zs5Ke6eptwnubIHKyi7...", created_at: "2018-08-27 23:42:26", updated_at: "2018-08-27 23:42:26">
```

#### Confirmations

For registering \(and numerous other purposes\), you might want to require the user to enter some information twice for verification. The user model already comes with this functionality.

For example, if we require the password to be entered twice:

```ruby
user1 = User.new.with_confirm(:password)
user1.username = 'admin'
user1.password = '123'
user1.save # Fail
user1.errors #=> # ... @messages={:password_confirmation=>["Passwords don't match"]}

user2 = User.new.with_confirm(:password)
user2.username = 'admin'
user2.password = '123'
user2.password_confirmation = '123'
user2.save # Success
#<User id: 1, username: "admin", encrypted_password: "$2a$10$jBtLScCHce2TPj6jvNFMWeAXfgV0rf0QAs/.omqtiIh...", ...>
```

The confirmation method will always be `<name of field>_confirmation`.

You can also pass multiple field symbols to the `with_confirm` method:

```ruby
user = User.new.with_confirm(:email, :password)
user.username = 'admin'
user.email = 'admin@test.com'
user.email_confirmation = 'admin@test.com'
user.password = '123'
user.password_confirmation = '123'
user.save # Success
```

### Authentication controller

Unless you used a specific flag during the authentication setup, an authentication controller will have been created.

This controller handles the routes for logging in or authenticating users, logging out users, and what to do when a page requiring authentication is accessed by an unauthenticated user.

### Authentication helpers

Three helper methods are defined during the authentication setup. Both are accessible in all controllers.

* `authenticate` - Permits an action to be performed if done by an authenticated user. If the user is not authenticated, they will be redirected.

  This is typically placed at the start of a route handler \(as seen in this example\):

  ```ruby
  class ProductController < Eucalypt::Controller(route: '/products')
    helpers ProductHelper if defined? ProductHelper
  
    # ...
  
    post '/:id/delete' do |id|
      authenticate
      product = Product.find id
      product.destroy!
      redirect to '/'
    rescue ActiveRecord::RecordNotFound
      status 404 # Resource not found
      redirect to "/#{id}"
    end
  end
  ```

* `current_user` - The user object of the currently authenticated user \(or false if no user is authenticated\). Since this isn't always an explicit boolean value, it is suggested to use the `authenticated?` method for conditionals. For example:

  ```ruby
  puts Product.all if authenticated? # Good
  puts Product.all if current_user   # Bad
  ```

* `authenticated?` alias `logged_in?` - Checks whether or not a user is currently authenticated or logged in. This should be used for conditionals rather than `current_user`, since it is always an explicit boolean value. This can be used in views for conditional displays.





