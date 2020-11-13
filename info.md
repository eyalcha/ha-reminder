## How it works
This script creates a sensor that counts down to the next occurrence of a reminder date.

Requires `python_script:` to be enabled in your configuration

## Installation
Copy the Python script in to your `/config/python_scripts` directory or install via HACS.

## Script arguments
key | required | type | description
-- | -- | -- | --
`name` | True | string | Name of the date (eg. John Birthday)
`date` | True | date |
`title` | False | string |

## Usage