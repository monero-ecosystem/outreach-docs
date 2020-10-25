# Monero Calendar API

There are a couple ways to retrieve data from the [Monero Calendar](https://www.monerooutreach.org/monero-calendar/), this section is a work in progress and we appreciate feedback to improve it. Please let us know if you find bugs or things missing.

### _iCalendar .ics_

**Upcoming Events** - Automatically updates and returns the next 30 days of events, up to 100. This file can be downloaded to import into the calendar of your choice manually or you can use the url to add it to your calendar as a subscription or manage it with a synchronizer.

```
https://calendar.monerooutreach.org/events.ics
```

**Events Query** - Generates an .ics file for events within a time range. This example is for August, 2020.

```
https://calendar.monerooutreach.org/##EpochStart##_##EpochEnd##.ics
https://calendar.monerooutreach.org/1596240000_1598918399.ics
```

Optionally you can add an event type filter. Currently all calendar events are either Meetings or Events

```
https://calendar.monerooutreach.org/##EpochStart##_##EpochEnd##_##Meetings|Events##.ics
https://calendar.monerooutreach.org/1596240000_1598918399_Events.ics
```

**Specific Event** - Generates an .ics file by unique event ID. This is what the calendar uses for specific events and can be sent to people to invite them to Monero events.

```
https://calendar.monerooutreach.org/##ID##.ics
https://calendar.monerooutreach.org/3fff989aJ.ics
```

### _JSON_

The events API is coming as part of a site-wide JSON output.