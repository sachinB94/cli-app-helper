# CliAppHelper

CliAppHelper helps you create command line apps with ease


# Features

- Reads arguments
- Supports flag aliases
- Show help using `--help` flag


# Install

```bash
$ pip install cliapphelper
```


# Usage
```bash
$ python sample.py --test value -r
```

```python
# sample.py
from CliAppHelper import CliAppHelper


cli_helper = CliAppHelper("""
    Usage
        $ sample <input>

    Options
        --test, -t Test flag
        --read, -r Read

    Examples
        $ sample --test value -r
""", {
    "flags": {
        "test": {
            "type": "string",
            "alias": "t"
        },
        "read": {
            "type": "boolean",
            "alias": "r",
            "default": True
        }
    }
})

flags = cli_helper.get_flags()
```


## API

### CliAppHelper(help_text, options)

Returns a class instance with:

- `get_flags` - Returns a dictionary with each flag and its value
- `show_help` - Shows help text

#### help_text

Type: `string`

Help text

#### options

Type: `dictionary`

##### flags

Type: `dictionary`

Argument flags.

The key is the flag name and the value is a dictionary with:

- `type`: Value type (`string` or `boolean`) - **Required**
- `alias`: Short flag (Example `r` for `read`)
- `default`: Default value


##### auto_help

Type: `boolean`

Default: `True`

Automatically show the help text when the `--help` flag is present.
