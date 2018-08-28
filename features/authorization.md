---
description: >-
  Authorization is the process of checking whether an authenticated user has the
  correct permissions to perform an action. It is handled by Pundit, and based
  around a concept called policies.
---

# Authorization

### Policies

Authorization is handled by simple, pure OO classes called policies. Policies are usually \(but not always\) linked to some model for which we wish to authorize the actions of.

Policies achieve authorization through the use of simple instance methods within the policy class. [Read this section of the Pundit readme for more information](https://github.com/varvet/pundit#policies).

#### CLI tasks

* [Policy](../cli/security/policy/)

#### Headless policies

As mentioned earlier, policies don't always have to be linked to a model. A policy of this kind is referred to as a **headless policy**.

A typical example of this would be a policy for authorizing general actions on a site, such as whether a certain type of user can access a part of the site. Since there is no model for the site itself, we use a headless policy.

A headless policy file is characterized by the class inheriting from a struct, like:

{% code-tabs %}
{% code-tabs-item title="app/policies/site\_policy.rb" %}
```ruby
class SitePolicy < Struct.new(:user, :site)
  def initialize(user, site)
    @user = user
    @site = site
  end
  
  # ...
end
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Non-headless policies

A typical policy is non-headless \(associated with a model\). For example, a `Product` model, which has permissions such as adding, editing and deleting a product.

The policy file looks similar to that of a headless policy file, but with no inheritance from a struct:

```ruby
class ProductPolicy
  def initialize(user, product)
    @user = user
    @product = product
  end
  
  # ...
end
```

### Models and tables

After [setting up authorization](../cli/security/pundit/setup.md), a `Role` model will have been created along with a `roles` table.

The purpose of the `roles` table is to specify the roles that a user has for each policy.

The `roles` table is a weak entity, with a one-to-one dependency on the `users` table. This means that every record in the `roles` table should be associated with a record in the `users` table. Additionally, whenever a user is deleted, the corresponding record in the `roles` will also be deleted.

An `after_create` callback is added to the `User` model after the authorization setup. This callback automatically creates a new record in the `roles` table when a new user is added to the `users` table.

#### Policy roles table

Each [generated policy](../cli/security/policy/generate.md) also comes with an associate policy roles table. For example, `eucalypt policy g post -p create edit delete` would generate a `post_policy.rb` file, and a `post_roles` table \(with create, edit and delete permissions\).

The columns in this table represent the different roles for the policy. For example, a post might have author and editor roles \(as well as an admin and default role, which every policy has by default\).

The rows in this table represent the different permissions that each role can have.

The `post_roles` table might look like:

|  | Admin | Default | Author | Editor |
| :--- | :--- | :--- | :--- | :--- |
| Create | `true` | `false` | `true` | `false` |
| Edit | `true` | `false` | `false` | `true` |
| Delete | `true` | `false` | `true` | `false` |

#### CLI tasks

* [Permission](../cli/security/policy/permission/generate.md)
* [Role](../cli/security/policy/role/generate.md)

### Authorization helper

During authorization setup, two helper methods were defined to help with authorization.

* The `authorized?` method was defined as a boolean method that specifies whether or not the currently authenticated user is authorized to perform an action on a certain policy.



  The `authorized?` method takes two arguments: 



  * The model object \(or class\) to check authorization for.

    If using a headless policy, this can also be a symbol.

  * The permission to check for. This is a symbol, a must end with a question mark `?`.

    The permission must be one of the permissions defined in the associated policy roles table. e.g. `:add?`, `edit?`, `delete?`



  The method returns false if there is no currently authenticated user, or if the authenticated user is not authorized to perform the specified action. The method returns true if the currently authenticated user is authorized to perform the specified action.



  For example:



  ```ruby
  # Non-headless policy, passing the model constant itself
  authorized? Post, :add?

  # Non-headless policy, passing an object
  post = Post.find(3)
  authorized? post, :edit?

  # Headless policy, passing a symbol
  authorized? :post, :delete?
  ```

  The `authorized?` method can be used in controllers and views \(for conditional displays\).

* The `authorize` method \(which comes as part of the Pundit gem\) permits an action to be performed if done by an authorized user.



  If the user is not authorized, then a `Pundit::NotAuthorizedError` is raised. This error can be handled however you like.



  This is typically placed somewhere in a route handler \(as seen in this example\):



  ```ruby
  class ProductController < Eucalypt::Controller(route: '/products')
  
    # ...
  
    post '/:id/delete' do |id|
      authenticate
      product = Product.find id
      authorize product, :delete?
      product.destroy!
      redirect to '/'
    rescue ActiveRecord::RecordNotFound
      status 404 # Resource not found
      redirect to "/#{id}"
    rescue Pundit::NotAuthorizedError
      status 401 # Unauthorized
      redirect to '/'
    end
  end
  ```







