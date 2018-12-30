# Configuration

### Description

The `config` directory contains more configurations in addition to those in the [core application file](../core-application-file.md). These configurations are stored in separate configuration files or directories:

* [Logging](logging.md) - `config/logging.rb`
* [Asset pipeline](asset-pipeline/) - `config/assets.rb`
* [Database](database.md) - `config/database.yml`
* [Initializers](initializers.md) - `config/initializers`

Other configuration files may also be generated with some `Eucalypt` commands. For example, [setting up authentication](../../cli/security/warden/setup.md) will generate a `config/warden.rb` file, or [setting up authorization](../../cli/security/pundit/setup.md) will generate a `config/pundit.rb` file.

