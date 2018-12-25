# Logging

### Logging

The configuration file can be found at `config/logging.rb`.

### Overview

Logging \(through the use of the `logger` helper\) will display a log message to STDOUT.

The logger has 6 severity levels:

```ruby
logger.unknown # Highest priority
logger.fatal   #        |
logger.error   #        |
logger.warn    #        |
logger.info    #        V
logger.debug   # Lowest priority
```

To write a log message, simply do:

```ruby
logger.info "This is a non-severe message."
```

By default, only messages above \(and equal to\) the `info` level will be displayed. This can be configured in the `config/logging.rb` file.

### Settings

The configuration file consists of a number of settings that can be used to adjust how logging works.

#### Environment-wide settings

The only setting that does not depend on the current environment is `:log_directory_format`. 

This setting specifies the `DateTime` string format for the sub-directory of the `logs` folder, where the current logs are being stored.

This defaults to `%Y-%m-%d_%H-%M-%S`, giving a `logs` folder structure like:

```text
logs
├── 2018-08-21_20-26-23
│   ├── production.stderr.log
│   └── production.stdout.log
└── 2018-08-21_20-26-41
    ├── development.stderr.log
    └── development.stdout.log
```

#### Environment-dependent settings

Logging can be fine-tuned according to the current environment. 

The configuration file contains a `configure` block for each environment. Each of these blocks can contain the following settings:

* `:logging` 
  * If set to `true` \(either with `set :logging, true` or `enable :logging`\), then logging is enabled via the `logger` helper method.

    When set to `true`, the [logger's severity level](https://github.com/bdurand/lumberjack/blob/master/lib/lumberjack/severity.rb) is set `INFO` by default.

  * If set to `false` \(either with `set :logging, false` or `disable :logging`\), then logging via the `logger` helper method is disabled - log messages get redirected to the [system's null device](https://en.wikipedia.org/wiki/Null_device).
  * If set to a `Lumberjack::Severity` level \(e.g. `set :logging, Lumberjack::Severity::FATAL`, or `set :logging, 4`\), then logging is enabled via the `logger` helper method, which is configured to only display log messages of the specified severity or lower.
* `:log_file`
  * If set to `true` \(either with `set :log_file, true` or `enable :log_file`\), then `STDOUT` and `STDERR` will be redirected to log files.
  * If set to `false` \(either with `set :log_file, false` or `disable :log_file`\), then `STDOUT` and `STDERR` will **not** be redirected to log files.

