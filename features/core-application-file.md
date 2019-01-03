---
description: >-
  The core application file contains the main configurations for your
  application, as well as require directives to various parts of your
  applications.
---

# Core application file

## Location

The core application file can be found at `app.rb`.

### Contents <a id="contents"></a>

The core application file contains the configurations for:

* The server used to run the application
* The default directory to look for views in
* The default view template to use for ERB
* The application root directory
* HTML and asset helpers

### Defining routes

Routes should generally not be defined in `ApplicationController` unless they are intended to be accessible by every other controller, which is rarely the case \(apart from error routes like `error Sinatra::NotFound do ... end`, which should typically redirect to a `/404` route defined in `MainController`\).

Core application routes such as the index `/` should instead be defined in `MainController`.

Alternatively, you can [generate a new controller](../cli/generate/controller.md).

