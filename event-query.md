# EventKoi — Event Query API

REST endpoint powering the Event Query Block, Event Series pages, and editor hydration.  
Provides event retrieval, calendar filtering, recurring instance expansion, exclusion rules, pagination, sorting, and date-range filters.

---

# Endpoint

```
GET /wp-json/eventkoi/v1/query_events
```

Public access via `REST::public_api`.

---

# Query Parameters

## Core Parameters

| Param               | Type   | Default    | Description                                                                                   |
| ------------------- | ------ | ---------- | --------------------------------------------------------------------------------------------- |
| `id`                | string | —          | Comma-separated calendar IDs. Example: `id=3,5,9`                                             |
| `include`           | string | —          | Comma-separated event IDs. Ignores calendars. Example: `include=12,40`                        |
| `parent_event`      | int    | —          | Expand and return **only** the instances of a specific event. Requires `include_instances=1`. |
| `include_instances` | bool   | `0`        | When `1`, expands recurring rules into standalone instances for **all modes**.                |
| `exclude`           | string | —          | Comma-separated recurring instance IDs. Only IDs containing “-” are recognized.               |
| `per_page`          | int    | `10`       | Number of events per page (`-1` for unlimited).                                               |
| `page`              | int    | `1`        | Page number.                                                                                  |
| `order`             | string | `desc`     | Sort direction (`asc` or `desc`).                                                             |
| `orderby`           | string | `modified` | Sort field: `modified`, `date`, or `title`.                                                   |
| `start_date`        | Y-m-d  | —          | WP-timezone filter start. Example: `start_date=2025-11-01`                                    |
| `end_date`          | Y-m-d  | —          | WP-timezone filter end. Example: `end_date=2025-11-30`                                        |

### Example — Events from multiple calendars

```
/wp-json/eventkoi/v1/query_events?id=2,4,7
```

### Example — Events in a date range

```
/wp-json/eventkoi/v1/query_events?start_date=2025-12-01&end_date=2025-12-31
```

---

## Special Modes

### `include`

Fetch specific event IDs (ignores calendars).

Example:

```
/wp-json/eventkoi/v1/query_events?include=12,45,90
```

With instances:

```
/wp-json/eventkoi/v1/query_events?include=12,45&include_instances=1
```

Response:

```json
{
  "events": [...],
  "total": 3,
  "source": "include"
}
```

---

### `include_instances`

Expands recurring rules into standalone instances.

Example:

```
/wp-json/eventkoi/v1/query_events?include_instances=1
```

Combined with multiple calendars:

```
/wp-json/eventkoi/v1/query_events?id=1,2,3&include_instances=1
```

---

### `parent_event`

Returns only the instances of a specific recurring event.

Example:

```
/wp-json/eventkoi/v1/query_events?parent_event=15&include_instances=1
```

With date filtering:

```
/wp-json/eventkoi/v1/query_events?parent_event=15&include_instances=1&start_date=2025-10-01&end_date=2025-10-31
```

---

### `exclude`

Exclude recurring instances by ID (must contain a hyphen).

Example:

```
exclude=22-1733090400,22-1734112200
```

Used like:

```
/wp-json/eventkoi/v1/query_events?id=2&include_instances=1&exclude=22-1733090400
```

---

# Query Modes

## 1. INCLUDE Mode (`?include=...`)

Triggered when `include` is present.

Example:

```
/wp-json/eventkoi/v1/query_events?include=5,9&include_instances=1
```

---

## 2. Parent Event Instances (`parent_event + include_instances`)

Example:

```
/wp-json/eventkoi/v1/query_events?parent_event=30&include_instances=1
```

Paginated:

```
/wp-json/eventkoi/v1/query_events?parent_event=30&include_instances=1&page=2&per_page=5
```

---

## 3. Default Calendar Query (no include & no parent_event)

Example:

```
/wp-json/eventkoi/v1/query_events?id=3&include_instances=1
```

With sorting:

```
/wp-json/eventkoi/v1/query_events?id=3&orderby=title&order=asc
```

---

# Recurring Events Logic

## When `include_instances=0`

Collapsed recurring parent example:

```
{
  "id": "12-base",
  "event_id": 12,
  "date_type": "recurring"
}
```

---

## When `include_instances=1`

Example endpoint expanding rules:

```
/wp-json/eventkoi/v1/query_events?id=4&include_instances=1
```

---

# Timestamp Fields

Every event contains:

| Field         | Meaning                       |
| ------------- | ----------------------------- |
| `start`       | UTC ISO8601 start             |
| `end`         | UTC ISO8601 end               |
| `start_ts`    | Start (UTC UNIX timestamp)    |
| `end_ts`      | End (UTC UNIX timestamp)      |
| `wp_start_ts` | Start adjusted to WP timezone |
| `wp_end_ts`   | End adjusted to WP timezone   |
| `timeline`    | Human-readable local timeline |
| `datetime`    | Display-friendly date/time    |
| `timezone`    | Event timezone (WP setting)   |

---

# Date Filtering Examples

Events overlapping November:

```
/wp-json/eventkoi/v1/query_events?start_date=2025-11-01&end_date=2025-11-30
```

Instances only during August:

```
/wp-json/eventkoi/v1/query_events?parent_event=50&include_instances=1&start_date=2025-08-01&end_date=2025-08-31
```

---

# Instance Exclusion Examples

Remove a specific instance:

```
/wp-json/eventkoi/v1/query_events?id=7&include_instances=1&exclude=7-1763029200
```

Remove multiple:

```
/wp-json/eventkoi/v1/query_events?id=7&include_instances=1&exclude=7-1763029200,7-1763634000
```

---

# Response Shapes

## Default Calendar Query

```json
{
  "calendar": {...},
  "count": 10,
  "total": 42,
  "page": 1,
  "per_page": 10,
  "events": [...],
  "source": "calendar"
}
```

## Include Mode

```json
{
  "events": [...],
  "total": 3,
  "source": "include"
}
```

## Parent Event Mode

```json
{
  "count": 6,
  "total": 12,
  "page": 1,
  "per_page": 10,
  "events": [...],
  "source": "parent_event"
}
```

---

# Notes

- All times are stored as UTC.
- Display components use `wp_start_ts` / `wp_end_ts`.
- Instance IDs follow `{eventID}-{timestamp}` format.
- Pagination happens **after** filtering & instance expansion.
