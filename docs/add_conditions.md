---
title: Add Conditions
layout: default
nav_order: 3
---

# Add Conditions

Add conditions can be used to control whether Dalek Mod should add a feature or not. 

For example, only adding if another mod is present, or only adding on specific occasions (Advent etc.)

## Mods

The `mods` condition allows you to only add when certain other mods are present.
```json
{
    "mods": [
        // List of modids to check. All mods in this list must be present.
    ]
}
```

## Dates

The `dates` condition allows you to only add on specific dates.

You can specify a list of dates with a `start` and `end`. If you don't specify an end, it will stay there indefinitely after the start date.

```json
{
    "dates": [
      {
        "start": { // The start date (required)
          "month": 11, // December
          "date": 25
        },
        "end": { // The end date (optional)
          "month": 11, // December
          "date": 26
        }
      }
    ]
}
```

The allowed properties for the dates are:
- `year`
- `month` (This is zero-indexed, so January is `0`)
- `date`
- `weekday` (`1` is Sunday, `2` is Monday, `7` is Saturday, etc.)
- `hour`
- `minute`

