---
layout: post
title: "Logging like a Lumberjack"
date: 2020-06-17 00:30:00 -0400
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559820489/js-code_n83m7a.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559820489/js-code_n83m7a.jpg
category: "Code"
tags:
  - Python
  - Logging
author: immanuelqrw
paginate: false
---
# Logging like a Lumberjack

[Standard Library Logging Tutorial](https://docs.python.org/3/howto/logging.html)

Logging is standard for any service based project where you would like to know what happened before an issue occurred. Theoretically of course, as most projects are scant with tools to debug or documentation.

Python's logging is almost entirely done through it's standard library's `logging` module, unlike Java's variety of different logging frameworks. This is due to Python's logging simplicity and most of the functionality modified strictly through configuration.

## Basic Configuration

Each language has a unique setup for logging, with Python using dictionary / file based configuration.

Logging has a default level, which decides what is written.

By default Python logs to the console, with the default level `WARNING`, indicating it will log anything of `WARNING` severity or higher. This can be modified to log more information to the console, or to files.

### To Console
```python
import logging
logging.warning('Watch out!')  # will print a message to the console
logging.info('I told you so')  # will not print anything
```

This logs messages of the default logging level and above to console.

### To File
```python
import logging
logging.basicConfig(filename='example.log',level=logging.DEBUG)
logging.debug('This message should go to the log file')
logging.info('So should this')
logging.warning('And this, too')
```

This logs these messages to the `example.log` file

### Levels

Levels are listening in ascending order to severity, with the designated level configuring the logger to write all higher severity messages.

| Level |
|:-----:|
| NOTSET |
| DEBUG |
| INFO |
| WARNING |
| ERROR |
| CRITICAL |

## Advanced Configuration

There's a lot of advanced configuration than can be covered, but I'll only focus on the configuration file.

The rest can be found in [Advanced Logging Tutorial](https://docs.python.org/3/howto/logging.html#advanced-logging-tutorial) portion of Python.

### Logger

Module level loggers are useful for tracking which module wrote which output. They can be maintained as singletons allowing one time setups.

```python
logger = logging.getLogger(__name__)
```

They also allow setting `Handlers` and `Filters` &rarr; useful for advanced formatting in logging.

### Configuration File

Configuration files can be in several formats: `conf`, `json`, `yaml`, etc.

Through `conf` files, you modify a `Logger` object through using the `fileConfig` [method](https://docs.python.org/3/library/logging.config.html#logging.config.fileConfig). This is a specific `shell-like` configuration format which allows setting values.

Similarly, `JSON` and `YAML` files can be used, but must be passed in through the `dictConfig` [method](https://docs.python.org/3/library/logging.config.html#logging.config.dictConfig). Data is passed after parsing a `JSON` or `YAML` file, then converting into a Python dictionary. This dictionary also has a specific [schema](https://docs.python.org/3/library/logging.config.html#dictionary-schema-details)

YAML Example:
```yaml
version: 1
formatters:
  simple:
    format: '%(asctime)s - %(name)s - %(levelname)s - %(message)s'
handlers:
  console:
    class: logging.StreamHandler
    level: DEBUG
    formatter: simple
    stream: ext://sys.stdout
loggers:
  simpleExample:
    level: DEBUG
    handlers: [console]
    propagate: no
root:
  level: DEBUG
  handlers: [console]
```

Overall, configuration has [many ways](https://docs.python.org/3/library/logging.config.html) to set it up.


## Alternatives

There are a few basic alternatives to logging, for specific use cases.

[print](https://docs.python.org/3/library/functions.html#print): classic Python `print` method, for ordinary usage

[warnings](https://docs.python.org/3/library/warnings.html): For avoidable issues

