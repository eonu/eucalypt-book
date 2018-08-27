# Logging

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

By default, only messages above \(and equal to\) the `info` level will be displayed. This can be configured in the [core application file](core-application-file.md).

### Development

If the application is running in the development environment, then all messages are displayed in the standard output \(STDOUT\).

### Production

If the application is running in the production environment:

* STDOUT is redirected to a log file \(`production.stdout.log`\)
* STDERR is redirected to a log file \(`production.stderr.log`\)

When the server is started, a new sub-directory is created within the `log` directory, where the name of the sub-directory is the full timestamp at the time of the server starting. 

The `production.stdout.log` and `production.stderr.log` files are placed within this sub-directory.

For example:

```text
log
├── 2018-08-21T20-26-23p0400
│   ├── production.stderr.log
│   └── production.stdout.log
└── 2018-08-21T20-26-41p0400
    ├── production.stderr.log
    └── production.stdout.log
```

### Test

If the application is running in the test environment:

* STDOUT is redirected to a log file \(`test.stdout.log`\)
* STDERR is redirected to a log file \(`test.stderr.log`\)

When the server is started, a new sub-directory is created within the `log` directory, where the name of the sub-directory is the full timestamp at the time of the server starting. 

The `test.stdout.log` and `test.stderr.log` files are placed within this sub-directory.

For example:

```text
log
├── 2018-08-21T20-26-23p0400
│   ├── test.stderr.log
│   └── test.stdout.log
└── 2018-08-21T20-26-41p0400
    ├── test.stderr.log
    └── test.stdout.log
```

