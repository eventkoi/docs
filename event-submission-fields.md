# EventKoi — Event Submission Field Reference

Reference for creating or importing `eventkoi_event` posts from tools like Gravity Forms, WPForms, custom REST integrations, or migration scripts.

This document focuses on the **field names**, **where they are stored**, and the **expected value shapes** so submitted events can be reviewed and approved safely.

---

# Storage Model

EventKoi events use:

1. **WordPress post fields**
2. **WordPress post meta**
3. **WordPress taxonomy terms**

## Post Type

```text
post_type = eventkoi_event
```

## Suggested approval workflow

For front-end submissions, create the event as:

```text
post_status = draft
```

or:

```text
post_status = pending
```

Then let an admin review and publish it.

---

# 1. Core WordPress Post Fields

These are regular WordPress post fields, not EventKoi meta.

| Field | Type | Notes |
| --- | --- | --- |
| `post_type` | string | Must be `eventkoi_event` |
| `post_title` | string | Event title |
| `post_status` | string | Usually `draft`, `pending`, or `publish` |

---

# 2. Core EventKoi Meta Fields

These are stored with `update_post_meta()` on the `eventkoi_event` post.

## Basic event info

| Meta key | Type | Example |
| --- | --- | --- |
| `description` | HTML/string | Full event description |
| `summary` | derived string | Generated from `description`; not a primary submission field |
| `image` | URL string | `https://example.com/image.jpg` |
| `image_id` | int | WordPress attachment ID |
| `template` | string | Template slug/selection |
| `timezone` | string | `UTC`, `Africa/Cairo`, `America/Los_Angeles` |
| `timezone_display` | bool | `true` or `false` |
| `tbc` | bool | `true` or `false` |
| `tbc_note` | string | Optional TBC display note |

---

# 3. Date Configuration

## Main selector

| Meta key | Type | Allowed values |
| --- | --- | --- |
| `date_type` | string | `standard` or `recurring` |

## Standard events only

| Meta key | Type | Allowed values |
| --- | --- | --- |
| `standard_type` | string | Usually `single` or `continuous` |
| `event_days` | array | Main structured date payload for standard events |

## Recurring events only

| Meta key | Type | Notes |
| --- | --- | --- |
| `recurrence_rules` | array | Main structured recurrence payload |

---

# 4. Standard Event Date Shape

For a normal non-recurring event, use:

```text
date_type = standard
standard_type = single
```

and store `event_days` like this:

```php
[
  [
    'start_date' => '2026-04-15T18:00:00Z',
    'end_date'   => '2026-04-15T20:00:00Z',
    'all_day'    => false,
  ],
]
```

## Recommended companion fields

These are also commonly stored and help keep the event data complete:

```php
start_date      = '2026-04-15 18:00:00'
end_date        = '2026-04-15 20:00:00'
start_date_iso  = '2026-04-15T18:00:00Z'
end_date_iso    = '2026-04-15T20:00:00Z'
start_timestamp = 1776276000
end_timestamp   = 1776283200
```

## Notes

- Save dates in **UTC** when possible.
- ISO UTC strings like `2026-04-15T18:00:00Z` are the safest format for imports/submissions.
- `all_day` must be a boolean.

---

# 5. Recurring Event Rule Shape

For recurring events, use:

```text
date_type = recurring
```

and store `recurrence_rules` like this:

```php
[
  [
    'start_date'        => '2026-04-15T18:00:00Z',
    'end_date'          => '2026-04-15T20:00:00Z',
    'all_day'           => false,
    'every'             => 1,
    'frequency'         => 'day',
    'working_days_only' => false,
    'ends'              => 'after',
    'ends_after'        => 10,
    'ends_on'           => '',
    'weekdays'          => [],
    'months'            => [],
    'month_day_rule'    => 'day-of-month',
    'month_day_value'   => 0,
  ],
]
```

## Allowed / expected values

### `frequency`

```text
day
week
month
year
```

### `ends`

```text
after
on
never
```

### `month_day_rule`

```text
day-of-month
weekday-of-month
```

### `weekdays`

Used mainly for weekly rules.
Typical values are weekday abbreviations such as:

```php
['MO', 'WE', 'FR']
```

### `months`

Used mainly for yearly rules.
Typically numeric month values:

```php
[1, 3, 6, 12]
```

---

# 6. Location Fields

## Source of truth

The main location field is:

```text
locations
```

This is an **array of location rows**.

## Physical location example

```php
[
  [
    'type'     => 'physical',
    'name'     => 'Main Hall',
    'address1' => '42 Market Street',
    'address2' => '',
    'address3' => '',
  ],
]
```

## Virtual location example

```php
[
  [
    'type'        => 'virtual',
    'name'        => 'Zoom',
    'virtual_url' => 'https://example.com/meeting',
    'link_text'   => 'Join event',
  ],
]
```

## Mixed event example

```php
[
  [
    'type'        => 'virtual',
    'name'        => 'Livestream',
    'virtual_url' => 'https://example.com/live',
    'link_text'   => 'Watch live',
  ],
  [
    'type'     => 'physical',
    'name'     => 'City Hall',
    'address1' => '125 King Street',
  ],
]
```

## Legacy location fields

These still exist for backward compatibility, but for new imports/submissions prefer `locations`:

- `location`
- `address1`
- `address2`
- `address3`
- `latitude`
- `longitude`
- `embed_gmap`
- `gmap_link`
- `virtual_url`

---

# 7. Calendar Assignment

Calendars are **taxonomy terms**, not plain meta.

Use taxonomy:

```text
event_cal
```

For example:

```php
wp_set_post_terms( $event_id, [ 12 ], 'event_cal', false );
```

---

# 8. Attendance Mode

| Meta key | Type | Allowed values |
| --- | --- | --- |
| `attendance_mode` | string | `none`, `rsvp`, `tickets` |

## RSVP-related meta

- `rsvp_enabled`
- `rsvp_capacity`
- `rsvp_show_remaining`
- `rsvp_allow_guests`
- `rsvp_max_guests`
- `rsvp_allow_edit`
- `rsvp_auto_account`

## Ticket-related meta

- `tickets_enabled`
- `tickets_require_account`
- `tickets_auto_create_account`
- `tickets_show_remaining`
- `tickets_show_unavailable`
- `tickets_terms_conditions`
- `tickets_display_mode`

---

# 9. Recommended Gravity Forms Strategy

For tools like Gravity Forms, do **not** try to map every field as a flat key/value feed only.

The safest flow is:

1. Create a WordPress post:
   - `post_type = eventkoi_event`
   - `post_status = draft` or `pending`
2. In `gform_after_submission`, map the submitted values into EventKoi meta.
3. Save structured arrays for:
   - `event_days`
   - `recurrence_rules`
   - `locations`
4. Assign calendar terms using `wp_set_post_terms()`.

## Why

Some EventKoi fields are not simple strings. These three are structured arrays and should be built intentionally:

- `event_days`
- `recurrence_rules`
- `locations`

---

# 10. Minimal Working Examples

## Minimal standard event

```php
wp_insert_post([
  'post_type'   => 'eventkoi_event',
  'post_status' => 'draft',
  'post_title'  => 'Submitted Event',
]);

update_post_meta( $event_id, 'date_type', 'standard' );
update_post_meta( $event_id, 'standard_type', 'single' );
update_post_meta( $event_id, 'event_days', [
  [
    'start_date' => '2026-04-15T18:00:00Z',
    'end_date'   => '2026-04-15T20:00:00Z',
    'all_day'    => false,
  ],
] );
update_post_meta( $event_id, 'locations', [
  [
    'type'     => 'physical',
    'name'     => 'Main Hall',
    'address1' => '42 Market Street',
  ],
] );
update_post_meta( $event_id, 'attendance_mode', 'none' );
```

## Minimal recurring event

```php
update_post_meta( $event_id, 'date_type', 'recurring' );
update_post_meta( $event_id, 'recurrence_rules', [
  [
    'start_date'        => '2026-04-15T18:00:00Z',
    'end_date'          => '2026-04-15T20:00:00Z',
    'all_day'           => false,
    'every'             => 1,
    'frequency'         => 'week',
    'working_days_only' => false,
    'ends'              => 'after',
    'ends_after'        => 6,
    'ends_on'           => '',
    'weekdays'          => [ 'MO' ],
    'months'            => [],
    'month_day_rule'    => 'day-of-month',
    'month_day_value'   => 0,
  ],
] );
```

---

# 11. Practical Recommendation

If you are building a public event submission form:

- save the event as `draft` or `pending`
- use UTC ISO datetimes
- use `locations` instead of legacy flat location fields
- use `event_days` for standard events
- use `recurrence_rules` for recurring events
- assign calendars through the `event_cal` taxonomy

That will produce the most reliable EventKoi-compatible submission flow.
