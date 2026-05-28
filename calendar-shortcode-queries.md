# EventKoi Calendar Shortcode Queries

Use the `[eventkoi_calendar]` shortcode to render a calendar or filtered event list on any WordPress page, post, or widget area that supports shortcodes.

This guide covers list-mode query parameters for upcoming events, past events, date ranges, ordering, pagination, result limits, and recurring instances.

---

## Basic List

```text
[eventkoi_calendar id="123" display="list"]
```

Replace `123` with the calendar ID.

---

## Upcoming Events

Upcoming events are events that start in the future.

```text
[eventkoi_calendar id="123" display="list" orderby="upcoming"]
```

When `orderby="upcoming"` is used without an `order` value, EventKoi sorts ascending by default, so the nearest upcoming event appears first.

```text
[eventkoi_calendar id="123" display="list" orderby="upcoming" order="asc"]
```

---

## Past Events

Past events are events that have already ended.

```text
[eventkoi_calendar id="123" display="list" orderby="past"]
```

EventKoi always sorts past events descending, so the most recent past event appears first.

The older alias `past_events` is also supported:

```text
[eventkoi_calendar id="123" display="list" orderby="past_events"]
```

Both examples render as `orderby="past"` internally.

---

## Date Ranges

Use `date_start` and `date_end` to limit the list to events that overlap a specific date range.

Dates use the WordPress site timezone and the `YYYY-MM-DD` format.

```text
[eventkoi_calendar id="123" display="list" date_start="2026-05-01" date_end="2026-05-31"]
```

You can combine date ranges with upcoming or past modes.

```text
[eventkoi_calendar id="123" display="list" orderby="upcoming" date_start="2036-01-01" date_end="2036-01-31"]
```

```text
[eventkoi_calendar id="123" display="list" orderby="past" date_start="2026-05-01" date_end="2026-05-31"]
```

---

## Sort by Event Start

Use `orderby="event_start"` when you want a pure start-date sort inside a range.

```text
[eventkoi_calendar id="123" display="list" orderby="event_start" order="asc" date_start="2036-01-01" date_end="2036-01-31"]
```

Descending:

```text
[eventkoi_calendar id="123" display="list" orderby="event_start" order="desc" date_start="2036-01-01" date_end="2036-01-31"]
```

The older alias `start_date` is also accepted and normalizes to `event_start`.

---

## Recurring Instances

EventKoi Pro can expand recurring events into individual instances in list mode.

```text
[eventkoi_calendar id="123" display="list" orderby="event_start" order="asc" date_start="2036-01-10" date_end="2036-01-12" expand_instances="true"]
```

This returns each matching recurring occurrence as its own list item.

You can also use the shorter alias:

```text
[eventkoi_calendar id="123" display="list" orderby="event_start" order="asc" date_start="2036-01-10" date_end="2036-01-12" expand="true"]
```

Recurring events are a Pro feature. EventKoi Lite supports the same non-recurring query parameters, but does not expand recurring events.

---

## Limit Results

Use `per_page` to control pagination size.

```text
[eventkoi_calendar id="123" display="list" orderby="upcoming" per_page="6"]
```

Use `max_results` to cap the total result set before pagination.

```text
[eventkoi_calendar id="123" display="list" orderby="event_start" order="asc" date_start="2036-01-01" date_end="2036-01-31" max_results="3"]
```

When recurring instances are expanded, EventKoi applies the date range and sort order before applying `max_results`.

---

## Supported Parameters

| Parameter | Example | Notes |
| --- | --- | --- |
| `id` | `id="123"` | Calendar ID. |
| `display` | `display="list"` | Query parameters in this guide apply to list mode. |
| `orderby` | `upcoming`, `past`, `event_start` | Also supports `past_events`, `start_date`, `title`, `publish_date`, `date`, `date_modified`, and `modified`. |
| `order` | `asc`, `desc` | `upcoming` defaults to `asc`; `past` is forced to `desc`. |
| `date_start` | `2026-05-01` | Start of the filter range in the WordPress site timezone. |
| `date_end` | `2026-05-31` | End of the filter range in the WordPress site timezone. |
| `per_page` | `10` | Number of events per page. |
| `max_results` | `3` | Maximum number of events returned across the whole result set. |
| `expand_instances` | `true` | Pro only. Expands recurring events into individual instances. |
| `expand` | `true` | Alias for `expand_instances`. |

---

## Pro and Lite Compatibility

EventKoi Pro and EventKoi Lite both support the shared list query parameters:

- `orderby="upcoming"`
- `orderby="past"`
- `orderby="past_events"`
- `orderby="event_start"`
- `order="asc"` / `order="desc"`
- `date_start`
- `date_end`
- `per_page`
- `max_results`

EventKoi Pro additionally supports recurring event expansion with `expand_instances="true"` or `expand="true"`.
