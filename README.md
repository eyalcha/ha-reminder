# Set Reminder

** THIS IS INITIAL VERSION, NOT FULLY TESTED YET!!! **

A python script for Home Assistant that counts down the days to reminder. ON the day of the reminder, the remminder state will be changed to on state.

[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)

## Script arguments
key | required | type | description
-- | -- | -- | --
`name` | True | string | Name of the date (eg. John Birthday)
`date` | True | date | Date, in format DD-MM-YYYY HH:MM (Time is optional)
`title` | False | string | Reminder title (will be used as the friendly name, default 'Reminder')
`recurrence` | False | string | yearly, montly, daily, does not repeat (default 'yearly')
`every` | False | number | Multiple of the recurrence period
`tag` | False | string | Tag
`notifier` | False | string | Notifer to call when reminder occurs
`script` | False | string | Script to execute when reminder occurs
`message` | False | string | Notifier message (default reminder title)

## Usage

examples:

```
name: John Birthday
date: 05-10-1985
title: John birthday
tag: birthday
```

or

```
name: Replace brita filter
date: 06-11-2020 08:00
recurrence: monthly
notifier: telegram_bot
```

or

```
name: Buy new running shoes
date: 01-10-2020 08:00
recurrence: monthly
every: 6
notifier: telegram_bot
```

## Generated sensors
Each sensor is given the following automatically:

```
entity_id: sensor.<name>
friendly_name: <title>
state: <on/off>
icon: <icon>
friendly_date: <YYYY-MM-DD HH:MM>
remaining: <Remaning days to occurence>
recurrence: <recurrence>
every: <every>
enable: <enable>
tag: <tag>
```

## Example configuration.yaml entry
An example automation to create and refresh the above three sensors daily would be:

```yaml
automation:
  - alias: Reminder refresh
    trigger:
      - platform: time_pattern
        minutes: 1
      - platform: homeassistant
        event: start
    action:
      - service: python_script.set_reminder
        data:
          name: John birthday
          date: "05-10-1985"
          title: John birthday
          tag: birthday
```

## Example Lovelace representation

```yaml
type: entities
show_header_toggle: false
title: Reminders
entities:
  - entity: sensor.john_birthday
```