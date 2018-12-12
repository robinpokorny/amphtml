<!--
Copyright 2017 The AMP HTML Authors. All Rights Reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS-IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# <a name="`amp-date-display`"></a> `amp-date-display`

<table>
  <tr>
    <td width="40%"><strong>Description</strong></td>
    <td>Display a sequence of backward counting to indicate the time remaining before an event is scheduled to occur.</td>
  </tr>
  <tr>
    <td><strong>Required Script</strong></td>
    <td><code>&lt;script async custom-element="amp-date-display" src="https://cdn.ampproject.org/v0/amp-date-display-0.1.js">&lt;/script></code></td>
  </tr>
  <tr>
    <td><strong><a href="https://www.ampproject.org/docs/guides/responsive/control_layout.html">Supported Layouts</a></strong></td>
    <td>fill, fixed, fixed-height, flex-item, nodisplay, responsive</td>
  </tr>
</table>

[TOC]

## Behavior

Please note the parsing rules of ISO date string.

### Example

```html
<amp-date-display
  datetime="2017-08-02T20:05:05.000Z"
  display-in="utc"
  layout="fixed" width="360" height="140">
  <template type="amp-mustache">
    <div>iso: {{iso}}</div>
    <div>day: {{day}} {{dayTwoDigit}} {{dayName}} {{dayNameShort}}</div>
    <div>month: {{month}} {{monthTwoDigit}} {{monthName}} {{monthNameShort}</div>
    <div>year: {{year}} {{yearTwoDigit}}</div>
    <div>hour: {{hour}} {{hourTwoDigit}} {{hour12}} {{hour12TwoDigit}} {{dayPeriod}}</div>
    <div>minute: {{minute}} {{minuteTwoDigit}}</div>
    <div>second: {{second}} {{secondTwoDigit}}</div>
  </template>
</amp-date-display>
```


### Returned time parameters

This table lists the format you can specify in your Mustache template:

Format | Meaning
-- | --
year | …, 1999, 2000, 2001, …,
yearTwoDigit | 00, 01, …, 99
month | 1, 2, …, 12
monthTwoDigit | 01, 02, …, 12
monthName | January, Febrary, … December (see `locale`)
monthNameShort | Jan, Feb, …, Dec (see `locale`)
day | 1, 2, …, 31
dayTwoDigit | 01, 02, …, 31
dayName | Monday, Tuesday, …, Sunday (see `locale`)
dayNameShort | Mon, Tue, Sun (see `locale`)
hour | 1, 2, …, 23
hourTwoDigit | 01, 02, …, 23
hour12 | 1, 2, …, 12
hour12TwoDigit | 01, 02, …, 23
minute | 1, 2, …, 59
minuteTwoDigit | 01, 02, …, 59
second | 1, 2, …, 59
secondTwoDigit | 01, 02, …, 59
dayPeriod | am, pm
iso | Simplified extended ISO format, '2001-02-03T04:05:06.007Z'

## Attributes

You must specify at least one of these required attributes: `datetime`, `timestamp-seconds`, `timestamp-ms`.

##### datetime

An ISO formatted date. For example, '2001-02-03T04:05:06.007+08:00'.

##### timestamp-seconds

A POSIX epoch value in seconds. For example, `timestamp-seconds="1521880470"`.

##### timestamp-ms

A POSIX epoch value in milliseconds. For example, `timestamp-ms="1521880470000"`.

##### offset-seconds (optional)

A positive or negative number that represents the number of seconds to add or subtract from the datetime. For example, `offset-seconds="60"` adds 60 seconds to the datetime.

##### display-in (optional)

The time zone that is used for displaying the date. If not present the local time zone of the user is taken.

Currently, the only supported value is `utc`.

##### locale (optional)

An internationalization language string for `monthName`, `dayNameShort`, `dayName`, and `dayNameShort`. The default value is `en` (for English).

## Validation
See [amp-date-display rules](https://github.com/ampproject/amphtml/blob/master/extensions/amp-date-display/validator-amp-date-display.protoascii) in the AMP validator specification.