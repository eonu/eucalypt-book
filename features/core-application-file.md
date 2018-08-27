---
description: >-
  The core application file contains the main configurations for your
  application, as well as require directives to various parts of your
  applications.
---

# Core application file



### Location {#location}

The core application file can be found at `app.rb`.

### Contents {#contents}

The core application file contains the configurations for:

* The server used to run the application
* The default directory to look for views in
* The default view template to use for ERB
* The application root directory
* HTML and asset helpers

### Defining routes

Note that although `app.rb` is a controller \(`ApplicationController`\), it is not advised to define routes in this file. The file `app/controllers/application_controller.rb` is meant for that purpose. Alternatively, you can [generate a new controller](../cli/generate/controller.md).

