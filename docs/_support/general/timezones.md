---
layout: section-page
title: "Timezones"
section: 02-02-02
tags: general
---

## Timezone Support in PatientWay Applications

Configuration:

- Set via the server's configuration (product specific)

Definitions:

* Date-time values - reference to a moment in time, usually precise to the day, minute, second
* Local date - a reference to a date (no time) using the currently configured timezone
* Local time - a reference to a moment in a day using the currently configured timezone

FYI

- PatientWay applications currently assume that all parts of the application operate in the same timezone
- All date-time values are stored in the database as UTC dates-time
- String dates are stored in the local timezone
- Local dates are expressed as "YYYY-MM-DD"
- Local times are expressed as "hh:mm"

Daylight Savings

- Daylight savings is automatically accounted for in most activities
- Hour of day reporting requires careful consideration
  - The transition to/from hours result in presentation headaches
  - Hourly totals for 2am will have a 1 day deficit or surplus when the date range includes an odd number of transition days.
  - Hourly averages for 2am will be inaccurate when there's an odd number of transition days. Adjust the demoninator plus or minus 1 as applicable

See 

[Impact of Daylight Saving Time
on the Clinical Laboratory](assets/daylight-savings-journal-article.pdf)

