# Set logging level with env


<!--more-->

# Set logging level with env

To set the logging level using an environment variable in Python, you can use the **`os`** module to read the value of the environment variable and pass it to the **`logging.basicConfig`** function.

Here is an example of how you can set the logging level using an environment variable in Python:

```jsx
import logging
import os

logging_level = os.environ.get('LOGGING_LEVEL', 'INFO')
logging.basicConfig(level=logging_level)

logging.debug('This is a debug message')
logging.info('This is an info message')
logging.warning('This is a warning message')
logging.error('This is an error message')
logging.critical('This is a critical message')
```

In this example, the logging level is set to **`INFO`** by default, but it can be overridden by setting the **`LOGGING_LEVEL`** environment variable to one of the following values: **`DEBUG`**, **`INFO`**, **`WARNING`**, **`ERROR`**, or **`CRITICAL`**.

For example, to set the logging level to **`DEBUG`**, you can set the **`LOGGING_LEVEL`** environment variable as follows:

```jsx
export LOGGING_LEVEL=DEBUG
```

You can then run your Python script and it will log messages at the **`DEBUG`**
 level and above.

