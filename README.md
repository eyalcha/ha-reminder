# Set Reminder
A python script for Home Assistant that counts down the days to reminder. ON the day of the reminder, the remminder state will be changed to on state.

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)

## Script arguments
key | required | type | description
-- | -- | -- | --
`name` | True | string | Name of the date (eg. John Birthday)
`icon` | False | string | Reminder icon (default mdi:calendar-star)
`date` | True | date |
`title` | False | string |
`recurrence` | False | string | yearly, montly, daily, does not repeat (default 'yearly')
`every` | False | number | Multiple of the recurrence period
`tag` | False | string | Tag
`notifier` | False | string | Notifer to call when reminder occurs
`script` | False | string | Script to execute when reminder occurs
`message` | False | string | Notifier message
`enable` | False |  | Enable / disable the reminder (default on)

## Usage