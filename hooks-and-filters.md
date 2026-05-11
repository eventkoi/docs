# EventKoi hooks & filters reference

Auto-generated inventory of every action and filter exposed by EventKoi Pro and Lite. Use these to extend the plugin without modifying core files. Each entry includes a description, a note on when the hook fires, the full signature, and the canonical source location.

- **Plugin column**:
  - *Pro + Lite* — same hook in both plugins
  - *Pro only* — Pro-only feature
  - *Lite only* — Lite-only (rare)
- **File** is the location of the **first occurrence** of each hook in the plugin source. A hook may fire from multiple call sites; the listed file is the canonical declaration.

## Contents
- [Events](#events) — 80 hooks (70 filters, 10 actions)
- [Calendars](#calendars) — 34 hooks (29 filters, 5 actions)
- [RSVPs](#rsvps) — 19 hooks (19 filters, 0 actions)
- [Tickets and orders](#tickets-and-orders) — 13 hooks (13 filters, 0 actions)
- [Blocks and shortcodes](#blocks-and-shortcodes) — 1 hooks (1 filters, 0 actions)
- [Page builders and loops](#page-builders-and-loops) — 2 hooks (2 filters, 0 actions)
- [Admin and UI](#admin-and-ui) — 3 hooks (2 filters, 1 actions)
- [Other](#other) — 53 hooks (43 filters, 10 actions)

## Events

### Filters

#### `eventkoi_beaver_event_options_limit`

_Pro + Lite · filter_

Filters the maximum number of events queried for the Beaver Builder event picker dropdown. Default 100.

**Fires:** When the BB picker requests its event list.

```php
apply_filters( 'eventkoi_beaver_event_options_limit', 200 );
```

- Pro: `includes/core/class-beaver-modules.php:422`
- Lite: `includes/core/class-beaver-modules.php:294`

#### `eventkoi_divi_event_options_limit`

_Pro + Lite · filter_

Filters the maximum number of events queried for the Divi event picker dropdown. Default 100.

**Fires:** When the Divi module loads its event-picker options.

```php
apply_filters( 'eventkoi_divi_event_options_limit', 200 );
```

- Pro: `includes/core/divi-modules/class-et-builder-module-eventkoievent.php:146`
- Lite: `includes/core/divi-modules/class-et-builder-module-eventkoievent.php:146`

#### `eventkoi_event_series_template_args`

_Pro + Lite · filter_

Filters the `$args` array passed to the event-series template.

**Fires:** On every event-series page render.

```php
apply_filters( 'eventkoi_event_series_template_args', $series_args ) );
```

- Pro: `includes/core/class-template.php:172`
- Lite: `includes/core/class-template.php:166`

#### `eventkoi_event_template_args`

_Pro + Lite · filter_

Filters the `$args` array passed to the resolved event template when rendering a single event. Use to inject extra variables that your custom template can read.

**Fires:** On every single-event page render.

```php
apply_filters( 'eventkoi_event_template_args', $args ) );
```

- Pro: `includes/core/class-template.php:161`
- Lite: `includes/core/class-template.php:155`

#### `eventkoi_get_default_event_template`

_Pro + Lite · filter_

Filters the default single-event template path used when no site-specific template override is set.

**Fires:** Once per single-event render fallback.

```php
apply_filters( 'eventkoi_get_default_event_template', $content );
```

- Pro: `includes/core/class-template.php:226`
- Lite: `includes/core/class-template.php:220`

#### `eventkoi_get_event_attendance_mode`

_Pro + Lite · filter_

Filters the event's `attendance_mode` value returned by `Event::get_attendance_mode()`. Override to change what `attendance_mode` resolves to for a given event.

**Fires:** On every call to `Event::get_attendance_mode()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_attendance_mode', $mode, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2475`
- Lite: `includes/core/class-event.php:1508`

#### `eventkoi_get_event_core_status`

_Pro + Lite · filter_

Filters the event's `core_status` value returned by `Event::get_core_status()`. Override to change what `core_status` resolves to for a given event.

**Fires:** On every call to `Event::get_core_status()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_core_status', $status, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1352`
- Lite: `includes/core/class-event.php:896`

#### `eventkoi_get_event_counts`

_Pro + Lite · filter_

Filters the event's `counts` value returned by `Event::get_counts()`. Override to change what `counts` resolves to for a given event.

**Fires:** On every call to `Event::get_counts()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_counts', $counts );
```

- Pro: `includes/core/class-events.php:2037`
- Lite: `includes/core/class-events.php:436`

#### `eventkoi_get_event_days`

_Pro + Lite · filter_

Filters the event's `days` value returned by `Event::get_days()`. Override to change what `days` resolves to for a given event.

**Fires:** On every call to `Event::get_days()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_days', $event_days, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:999`
- Lite: `includes/core/class-event.php:633`

#### `eventkoi_get_event_description`

_Pro + Lite · filter_

Filters the event's `description` value returned by `Event::get_description()`. Override to change what `description` resolves to for a given event.

**Fires:** On every call to `Event::get_description()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_description', wp_kses_post( $description ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1159`
- Lite: `includes/core/class-event.php:711`

#### `eventkoi_get_event_dynamic_tags`

_Pro only · filter_

Filters the event's `dynamic_tags` value returned by `Event::get_dynamic_tags()`. Override to change what `dynamic_tags` resolves to for a given event.

**Fires:** On every call to `Event::get_dynamic_tags()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_dynamic_tags', $tags );
```

- Pro: `includes/core/class-elementor-dynamic-tags.php:306`

#### `eventkoi_get_event_embed_gmap`

_Pro + Lite · filter_

Filters the event's `embed_gmap` value returned by `Event::get_embed_gmap()`. Override to change what `embed_gmap` resolves to for a given event.

**Fires:** On every call to `Event::get_embed_gmap()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_embed_gmap', (bool) $embed_gmap, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2273`
- Lite: `includes/core/class-event.php:1476`

#### `eventkoi_get_event_end_date_iso`

_Pro + Lite · filter_

Filters the event's `end_date_iso` value returned by `Event::get_end_date_iso()`. Override to change what `end_date_iso` resolves to for a given event.

**Fires:** On every call to `Event::get_end_date_iso()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_end_date_iso', $iso, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1605`
- Lite: `includes/core/class-event.php:1137`

#### `eventkoi_get_event_end_date_raw`

_Pro + Lite · filter_

Filters the event's `end_date_raw` value returned by `Event::get_end_date_raw()`. Override to change what `end_date_raw` resolves to for a given event.

**Fires:** On every call to `Event::get_end_date_raw()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_end_date_raw', (string) $formatted, self::$event_id, self::$event, $gmt );
```

- Pro: `includes/core/class-event.php:1505`
- Lite: `includes/core/class-event.php:1043`

#### `eventkoi_get_event_gmap_link`

_Pro + Lite · filter_

Filters the event's `gmap_link` value returned by `Event::get_gmap_link()`. Override to change what `gmap_link` resolves to for a given event.

**Fires:** On every call to `Event::get_gmap_link()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_gmap_link', (string) $gmap_link, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2282`
- Lite: `includes/core/class-event.php:1485`

#### `eventkoi_get_event_ical`

_Pro + Lite · filter_

Filters the event's `ical` value returned by `Event::get_ical()`. Override to change what `ical` resolves to for a given event.

**Fires:** On every call to `Event::get_ical()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_ical', $ical, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1301`
- Lite: `includes/core/class-event.php:848`

#### `eventkoi_get_event_id`

_Pro + Lite · filter_

Filters the event's `id` value returned by `Event::get_id()`. Override to change what `id` resolves to for a given event.

**Fires:** On every call to `Event::get_id()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_id', $id, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:966`
- Lite: `includes/core/class-event.php:600`

#### `eventkoi_get_event_image`

_Pro + Lite · filter_

Filters the event's `image` value returned by `Event::get_image()`. Override to change what `image` resolves to for a given event.

**Fires:** On every call to `Event::get_image()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_image', esc_url( $attachment_url ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1173`
- Lite: `includes/core/class-event.php:727`

#### `eventkoi_get_event_image_id`

_Pro + Lite · filter_

Filters the event's `image_id` value returned by `Event::get_image_id()`. Override to change what `image_id` resolves to for a given event.

**Fires:** On every call to `Event::get_image_id()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_image_id', absint( $image_id ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1215`
- Lite: `includes/core/class-event.php:764`

#### `eventkoi_get_event_image_thumb`

_Pro + Lite · filter_

Filters the event's `image_thumb` value returned by `Event::get_image_thumb()`. Override to change what `image_thumb` resolves to for a given event.

**Fires:** On every call to `Event::get_image_thumb()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_image_thumb', esc_url( $thumb ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1206`
- Lite: `includes/core/class-event.php:755`

#### `eventkoi_get_event_latitude`

_Pro + Lite · filter_

Filters the event's `latitude` value returned by `Event::get_latitude()`. Override to change what `latitude` resolves to for a given event.

**Fires:** On every call to `Event::get_latitude()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_latitude', (string) $latitude, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2255`
- Lite: `includes/core/class-event.php:1458`

#### `eventkoi_get_event_location`

_Pro + Lite · filter_

Filters the event's `location` value returned by `Event::get_location()`. Override to change what `location` resolves to for a given event.

**Fires:** On every call to `Event::get_location()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_location', $location, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2246`
- Lite: `includes/core/class-event.php:1449`

#### `eventkoi_get_event_locations`

_Pro + Lite · filter_

Filters the event's `locations` value returned by `Event::get_locations()`. Override to change what `locations` resolves to for a given event.

**Fires:** On every call to `Event::get_locations()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_locations', $locations, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1230`
- Lite: `includes/core/class-event.php:779`

#### `eventkoi_get_event_longitude`

_Pro + Lite · filter_

Filters the event's `longitude` value returned by `Event::get_longitude()`. Override to change what `longitude` resolves to for a given event.

**Fires:** On every call to `Event::get_longitude()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_longitude', (string) $longitude, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2264`
- Lite: `includes/core/class-event.php:1467`

#### `eventkoi_get_event_meta`

_Pro + Lite · filter_

Filters the event's `meta` value returned by `Event::get_meta()`. Override to change what `meta` resolves to for a given event.

**Fires:** On every call to `Event::get_meta()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_meta', $meta, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:195`
- Lite: `includes/core/class-event.php:186`

#### `eventkoi_get_event_post_status`

_Pro + Lite · filter_

Filters the event's `post_status` value returned by `Event::get_post_status()`. Override to change what `post_status` resolves to for a given event.

**Fires:** On every call to `Event::get_post_status()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_post_status', $post_status, $event_id );
```

- Pro: `includes/core/core-functions.php:161`
- Lite: `includes/core/core-functions.php:113`

#### `eventkoi_get_event_recurrence_overrides`

_Pro + Lite · filter_

Filters the event's `recurrence_overrides` value returned by `Event::get_recurrence_overrides()`. Override to change what `recurrence_overrides` resolves to for a given event.

**Fires:** On every call to `Event::get_recurrence_overrides()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_recurrence_overrides', $overrides, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1084`
- Lite: `includes/core/class-event.php:673`

#### `eventkoi_get_event_recurrence_rules`

_Pro + Lite · filter_

Filters the event's `recurrence_rules` value returned by `Event::get_recurrence_rules()`. Override to change what `recurrence_rules` resolves to for a given event.

**Fires:** On every call to `Event::get_recurrence_rules()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_recurrence_rules', $rules, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1059`
- Lite: `includes/core/class-event.php:648`

#### `eventkoi_get_event_schema`

_Pro + Lite · filter_

Filters the JSON-LD `Event` schema array emitted into the head of an event page. Use to add organiser, performer, offer, or custom schema fields beyond what EventKoi populates by default.

**Fires:** From `Schema::render()` just before `wp_json_encode()`, on every single-event page render.

```php
apply_filters( 'eventkoi_get_event_schema', $schema );
```

- Pro: `includes/core/class-schema.php:190`
- Lite: `includes/core/class-schema.php:190`

#### `eventkoi_get_event_series_template`

_Pro + Lite · filter_

Filters the absolute path of the template file used to render an event series. Override to ship your own template from a theme.

**Fires:** Once per series page render, before `include`.

```php
apply_filters( 'eventkoi_get_event_series_template', $content );
```

- Pro: `includes/core/class-template.php:300`
- Lite: `includes/core/class-template.php:294`

#### `eventkoi_get_event_standard_type`

_Pro + Lite · filter_

Filters the event's `standard_type` value returned by `Event::get_standard_type()`. Override to change what `standard_type` resolves to for a given event.

**Fires:** On every call to `Event::get_standard_type()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_standard_type', (string) $standard_type, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2218`
- Lite: `includes/core/class-event.php:1435`

#### `eventkoi_get_event_start_date_iso`

_Pro + Lite · filter_

Filters the event's `start_date_iso` value returned by `Event::get_start_date_iso()`. Override to change what `start_date_iso` resolves to for a given event.

**Fires:** On every call to `Event::get_start_date_iso()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_start_date_iso', $iso, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1572`
- Lite: `includes/core/class-event.php:1104`

#### `eventkoi_get_event_start_date_raw`

_Pro + Lite · filter_

Filters the event's `start_date_raw` value returned by `Event::get_start_date_raw()`. Override to change what `start_date_raw` resolves to for a given event.

**Fires:** On every call to `Event::get_start_date_raw()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_start_date_raw', (string) $formatted, self::$event_id, self::$event, $gmt );
```

- Pro: `includes/core/class-event.php:1439`
- Lite: `includes/core/class-event.php:983`

#### `eventkoi_get_event_status`

_Pro + Lite · filter_

Filters the event's `status` value returned by `Event::get_status()`. Override to change what `status` resolves to for a given event.

**Fires:** On every call to `Event::get_status()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_status', $status, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1343`
- Lite: `includes/core/class-event.php:887`

#### `eventkoi_get_event_tbc`

_Pro + Lite · filter_

Filters the event's `tbc` value returned by `Event::get_tbc()`. Override to change what `tbc` resolves to for a given event.

**Fires:** On every call to `Event::get_tbc()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_tbc', (bool) $tbc, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2084`
- Lite: `includes/core/class-event.php:1229`

#### `eventkoi_get_event_tbc_note`

_Pro + Lite · filter_

Filters the event's `tbc_note` value returned by `Event::get_tbc_note()`. Override to change what `tbc_note` resolves to for a given event.

**Fires:** On every call to `Event::get_tbc_note()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_tbc_note', (string) $tbc_note, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2102`
- Lite: `includes/core/class-event.php:1247`

#### `eventkoi_get_event_thumbnail`

_Pro + Lite · filter_

Filters the event's `thumbnail` value returned by `Event::get_thumbnail()`. Override to change what `thumbnail` resolves to for a given event.

**Fires:** On every call to `Event::get_thumbnail()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_thumbnail', esc_url( $thumbnail ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1095`
- Lite: `includes/core/class-event.php:684`

#### `eventkoi_get_event_timezone`

_Pro + Lite · filter_

Filters the event's `timezone` value returned by `Event::get_timezone()`. Override to change what `timezone` resolves to for a given event.

**Fires:** On every call to `Event::get_timezone()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_timezone', (string) $timezone, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:977`
- Lite: `includes/core/class-event.php:611`

#### `eventkoi_get_event_title`

_Pro + Lite · filter_

Filters the event's `title` value returned by `Event::get_title()`. Override to change what `title` resolves to for a given event.

**Fires:** On every call to `Event::get_title()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_title', $title, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1150`
- Lite: `includes/core/class-event.php:702`

#### `eventkoi_get_event_type`

_Pro + Lite · filter_

Filters the event's `type` value returned by `Event::get_type()`. Override to change what `type` resolves to for a given event.

**Fires:** On every call to `Event::get_type()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_type', (string) $type, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2186`
- Lite: `includes/core/class-event.php:1422`

#### `eventkoi_get_event_url`

_Pro + Lite · filter_

Filters the event's `url` value returned by `Event::get_url()`. Override to change what `url` resolves to for a given event.

**Fires:** On every call to `Event::get_url()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_url', $url, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1283`
- Lite: `includes/core/class-event.php:830`

#### `eventkoi_get_event_virtual_url`

_Pro + Lite · filter_

Filters the event's `virtual_url` value returned by `Event::get_virtual_url()`. Override to change what `virtual_url` resolves to for a given event.

**Fires:** On every call to `Event::get_virtual_url()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_virtual_url', (string) $virtual_url, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2291`
- Lite: `includes/core/class-event.php:1494`

#### `eventkoi_get_summary`

_Pro + Lite · filter_

Filters the event excerpt/summary returned by `Event::get_summary()`. Receives `($summary, $event_id, $event)`.

**Fires:** Once per call to `Event::get_summary()`.

```php
apply_filters( 'eventkoi_get_summary', $summary, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2778`
- Lite: `includes/core/class-event.php:1908`

#### `eventkoi_get_summary_from_string`

_Pro only · filter_

Filters the cleaned-up summary text produced by `eventkoi_get_summary_from_string()` (used by REST responses and instance overrides).

**Fires:** Once per call to the helper.

```php
apply_filters( 'eventkoi_get_summary_from_string', $content, $max_chars );
```

- Pro: `includes/core/core-functions.php:134`

#### `eventkoi_pre_update_event_meta`

_Pro + Lite · filter_

Filters the meta array passed into `Event::update()` before any fields are persisted. Use to inject computed defaults or sanitize incoming values upfront.

**Fires:** Once per event create/update.

```php
apply_filters( 'eventkoi_pre_update_event_meta', $meta, $meta['id'] );
```

- Pro: `includes/core/class-event.php:672`
- Lite: `includes/core/class-event.php:389`

#### `eventkoi_rendered_event_capacity`

_Pro + Lite · filter_

Filters the rendered output of the `{event_capacity}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('capacity')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_capacity', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3758`
- Lite: `includes/core/class-event.php:2851`

#### `eventkoi_rendered_event_capacity_remaining`

_Pro + Lite · filter_

Filters the rendered output of the `{event_capacity_remaining}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('capacity_remaining')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_capacity_remaining', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3769`
- Lite: `includes/core/class-event.php:2862`

#### `eventkoi_rendered_event_capacity_sold`

_Pro + Lite · filter_

Filters the rendered output of the `{event_capacity_sold}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('capacity_sold')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_capacity_sold', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3780`
- Lite: `includes/core/class-event.php:2873`

#### `eventkoi_rendered_event_date`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3285`
- Lite: `includes/core/class-event.php:2407`

#### `eventkoi_rendered_event_date_day`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_day}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_day')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_day', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4097`
- Lite: `includes/core/class-event.php:3177`

#### `eventkoi_rendered_event_date_day_name`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_day_name}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_day_name')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_day_name', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4108`
- Lite: `includes/core/class-event.php:3188`

#### `eventkoi_rendered_event_date_iso`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_iso}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_iso')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_iso', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4119`
- Lite: `includes/core/class-event.php:3199`

#### `eventkoi_rendered_event_date_month`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_month}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_month')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_month', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4075`
- Lite: `includes/core/class-event.php:3155`

#### `eventkoi_rendered_event_date_month_short`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_month_short}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_month_short')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_month_short', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4086`
- Lite: `includes/core/class-event.php:3166`

#### `eventkoi_rendered_event_date_year`

_Pro + Lite · filter_

Filters the rendered output of the `{event_date_year}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('date_year')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_date_year', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4064`
- Lite: `includes/core/class-event.php:3144`

#### `eventkoi_rendered_event_datetime`

_Pro + Lite · filter_

Filters the rendered output of the `{event_datetime}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('datetime')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_datetime', $message, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3162`
- Lite: `includes/core/class-event.php:2291`

#### `eventkoi_rendered_event_datetime_with_summary`

_Pro + Lite · filter_

Filters the rendered output of the `{event_datetime_with_summary}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('datetime_with_summary')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_datetime_with_summary', wp_kses_post( $line ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3190`
- Lite: `includes/core/class-event.php:2314`

#### `eventkoi_rendered_event_details`

_Pro + Lite · filter_

Filters the rendered output of the `{event_details}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('details')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_details', $details, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2857`
- Lite: `includes/core/class-event.php:1986`

#### `eventkoi_rendered_event_image_url`

_Pro + Lite · filter_

Filters the rendered output of the `{event_image_url}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('image_url')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_image_url', $url, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2913`
- Lite: `includes/core/class-event.php:2042`

#### `eventkoi_rendered_event_location`

_Pro + Lite · filter_

Filters the rendered output of the `{event_location}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('location')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_location', implode( "\n\n", $outputs ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3055`
- Lite: `includes/core/class-event.php:2184`

#### `eventkoi_rendered_event_low_stock`

_Pro + Lite · filter_

Filters the rendered output of the `{event_low_stock}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('low_stock')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_low_stock', '', self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3806`
- Lite: `includes/core/class-event.php:2899`

#### `eventkoi_rendered_event_sales_end`

_Pro + Lite · filter_

Filters the rendered output of the `{event_sales_end}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('sales_end')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_sales_end', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3904`
- Lite: `includes/core/class-event.php:2994`

#### `eventkoi_rendered_event_sales_start`

_Pro + Lite · filter_

Filters the rendered output of the `{event_sales_start}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('sales_start')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_sales_start', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3879`
- Lite: `includes/core/class-event.php:2969`

#### `eventkoi_rendered_event_sold_out`

_Pro + Lite · filter_

Filters the rendered output of the `{event_sold_out}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('sold_out')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_sold_out', $label, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3792`
- Lite: `includes/core/class-event.php:2885`

#### `eventkoi_rendered_event_time`

_Pro + Lite · filter_

Filters the rendered output of the `{event_time}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('time')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_time', '', self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3336`
- Lite: `includes/core/class-event.php:2458`

#### `eventkoi_rendered_event_timezone`

_Pro + Lite · filter_

Filters the rendered output of the `{event_timezone}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('timezone')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_timezone', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3096`
- Lite: `includes/core/class-event.php:2225`

#### `eventkoi_rendered_event_title`

_Pro + Lite · filter_

Filters the rendered output of the `{event_title}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('title')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_title', $title, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2838`
- Lite: `includes/core/class-event.php:1968`

#### `eventkoi_rendered_event_type`

_Pro only · filter_

Filters the rendered output of the `{event_type}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('type')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_type', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2205`

#### `eventkoi_taxonomy_objects_event_cal`

_Pro + Lite · filter_

Filters the array of post types attached to the `event_cal` taxonomy. Default is `['eventkoi_event']`. Add post types here to let them share calendars with events.

**Fires:** Once at taxonomy registration time.

```php
apply_filters( 'eventkoi_taxonomy_objects_event_cal', array( 'eventkoi_event' ) ),
			apply_filters(
				'eventkoi_taxonomy_args_event_cal', array(
					'hierarchical'          => true,
					'update_count_callback' => '_update_post_term_count',
					'label'                 => __( 'Calendars', 'eventkoi' ),
					'labels'                => array(
						'name'                  => __( 'Event calendars', 'eventkoi' ),
						'singular_name'         => __( 'Calendar', 'eventkoi' ),
						'menu_name'             => _x( 'Calendars', 'Admin menu name', 'eventkoi' ),
						'search_items'          => __( 'Search calendars', 'eventkoi' ),
						'all_items'             => __( 'All calendars', 'eventkoi' ),
						'parent_item'           => __( 'Parent calendar', 'eventkoi' ),
						'parent_item_colon'     => __( 'Parent calendar:', 'eventkoi' ),
						'edit_item'             => __( 'Edit calendar', 'eventkoi' ),
						'update_item'           => __( 'Update calendar', 'eventkoi' ),
						'add_new_item'          => __( 'Add new calendar', 'eventkoi' ),
						'new_item_name'         => __( 'New calendar name', 'eventkoi' ),
						'not_found'             => __( 'No calendars found', 'eventkoi' ),
						'item_link'             => __( 'Event Calendar Link', 'eventkoi' ),
						'item_link_description' => __( 'A link to a event calendar.', 'eventkoi' ),
						'template_name'         => _x( 'Events by Calendar', 'Template name', 'eventkoi' ),
					),
					'show_in_rest'          => true,
					'show_ui'               => true,
					'query_var'             => true,
					'rewrite'               => array(
						'slug'         => $permalinks['category_rewrite_slug'],
						'with_front'   => false,
						'hierarchical' => true,
					),
				)
			) );
```

- Pro: `includes/core/class-post-types.php:48`
- Lite: `includes/core/class-post-types.php:48`

#### `eventkoi_update_event_meta`

_Pro + Lite · filter_

Filters the meta array inside `Event::update_meta()` (and `Calendar::update_meta()`) right before any meta keys are written. Last chance to mutate the values that will be persisted. Despite the name, this filter also fires for calendars.

**Fires:** Once per event/calendar meta save.

```php
apply_filters( 'eventkoi_update_event_meta', $meta, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:466`
- Lite: `includes/core/class-calendar.php:334`

### Actions

#### `eventkoi_after_event_content`

_Pro + Lite · action_

Fires inside the legacy single-event template, after the event content loop and `eventkoi_single_event_template`, before the footer.

**Fires:** Once per legacy single-event render.

```php
do_action( 'eventkoi_after_event_content' );
```

- Pro: `templates/single-event-legacy.php:41`
- Lite: `templates/single-event-legacy.php:41`

#### `eventkoi_after_events_deleted`

_Pro + Lite · action_

Fires after the bulk `delete_events` REST handler soft-deletes one or more events (moves to trash). Receives the array of post IDs.

**Fires:** On every bulk-delete REST call from the events list.

```php
do_action( 'eventkoi_after_events_deleted', $ids );
```

- Pro: `includes/api/class-events.php:208`
- Lite: `includes/api/class-events.php:194`

#### `eventkoi_after_events_duplicated`

_Pro + Lite · action_

Fires after the bulk `duplicate_events` REST handler clones one or more events. Receives the array of source (original) post IDs.

**Fires:** On every bulk-duplicate REST call from the events list.

```php
do_action( 'eventkoi_after_events_duplicated', $ids );
```

- Pro: `includes/api/class-events.php:282`
- Lite: `includes/api/class-events.php:268`

#### `eventkoi_after_events_removed`

_Pro + Lite · action_

Fires after the bulk `remove_events` REST handler permanently removes one or more events. Receives the array of post IDs.

**Fires:** On every bulk-remove REST call from the trash view.

```php
do_action( 'eventkoi_after_events_removed', $ids );
```

- Pro: `includes/api/class-events.php:230`
- Lite: `includes/api/class-events.php:216`

#### `eventkoi_after_events_restored`

_Pro + Lite · action_

Fires after the bulk `restore_events` REST handler restores one or more events from trash. Receives the array of post IDs.

**Fires:** On every bulk-restore REST call from the trash view.

```php
do_action( 'eventkoi_after_events_restored', $ids );
```

- Pro: `includes/api/class-events.php:252`
- Lite: `includes/api/class-events.php:238`

#### `eventkoi_after_update_event_meta`

_Pro + Lite · action_

Fires inside `Event::update_meta()` after every post meta key has been written and calendar terms have been assigned. Receives the meta array, event ID, and post object.

**Fires:** Once per event meta save.

```php
do_action( 'eventkoi_after_update_event_meta', $meta, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:957`
- Lite: `includes/core/class-event.php:591`

#### `eventkoi_before_event_content`

_Pro + Lite · action_

Fires inside the legacy single-event template, immediately after the header and before the event content loop.

**Fires:** Once per legacy single-event render. (Block-theme renders use the block template hook chain instead.)

```php
do_action( 'eventkoi_before_event_content' );
```

- Pro: `templates/single-event-legacy.php:32`
- Lite: `templates/single-event-legacy.php:32`

#### `eventkoi_before_update_event_meta`

_Pro + Lite · action_

Fires inside `Event::update_meta()` after the incoming meta has been filtered, but before any post meta is written. Receives the filtered meta, event ID, and post object.

**Fires:** Once per event meta save.

```php
do_action( 'eventkoi_before_update_event_meta', $meta, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:733`
- Lite: `includes/core/class-event.php:450`

#### `eventkoi_event_posts_migrated`

_Pro + Lite · action_

Fires after the legacy → `eventkoi_event` post type migration completes. Receives the count of migrated posts.

**Fires:** Once per migration run (from a one-shot upgrade routine).

```php
do_action( 'eventkoi_event_posts_migrated', count( $post_ids ) );
```

- Pro: `includes/core/class-install.php:274`
- Lite: `includes/core/class-install.php:257`

#### `eventkoi_single_event_template`

_Pro + Lite · action_

Fires inside the legacy single-event template, inside the loop, after the event content is echoed. Receives the current `$post` object as its sole argument.

**Fires:** Once per matched post inside the legacy single-event render.

```php
do_action( 'eventkoi_single_event_template', $post );
```

- Pro: `templates/single-event-legacy.php:37`
- Lite: `templates/single-event-legacy.php:37`

## Calendars

### Filters

#### `eventkoi_calendar_display_max_results`

_Pro only · filter_

Filters the cap on number of events fetched per calendar render, based on the FullCalendar view type and date window. Receives `($max_results, $context_array)`.

**Fires:** Once per calendar `events` REST call.

```php
apply_filters( 'eventkoi_calendar_display_max_results', $max_results, array(
					'view_type'    => $view_type,
					'window_days'  => $window_days,
					'calendar_id'  => absint( $id ),
					'calendar_ids' => $ids,
				) );
```

- Pro: `includes/api/class-calendar.php:288`

#### `eventkoi_default_calendar_color`

_Pro + Lite · filter_

Filters the default hex color (`#578CA7`) used when a calendar has no color set. Useful for matching brand defaults across new sites.

**Fires:** Once per call to `eventkoi_default_calendar_color()`.

```php
apply_filters( 'eventkoi_default_calendar_color', '#578CA7' );
```

- Pro: `includes/core/core-functions.php:845`
- Lite: `includes/core/core-functions.php:775`

#### `eventkoi_get_calendar_color`

_Pro + Lite · filter_

Filters the calendar's `color` value returned by `Calendar::get_color()`.

**Fires:** On every call to `Calendar::get_color()`.

```php
apply_filters( 'eventkoi_get_calendar_color', $color, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:384`
- Lite: `includes/core/class-calendar.php:252`

#### `eventkoi_get_calendar_content`

_Pro + Lite · filter_

Filters the assembled `<!-- wp:group -->` template for the calendar or list block right before `do_blocks()` runs. Useful for adding wrapper attributes, debug markers, or parking-lot HTML around the FullCalendar container.

**Fires:** Once per calendar/list block render and once per `[eventkoi]` shortcode render.

```php
apply_filters( 'eventkoi_get_calendar_content', $calendar_template ) );
```

- Pro: `includes/core/core-functions.php:546`
- Lite: `includes/core/core-functions.php:476`

#### `eventkoi_get_calendar_count`

_Pro + Lite · filter_

Filters the calendar's `count` value returned by `Calendar::get_count()`.

**Fires:** On every call to `Calendar::get_count()`.

```php
apply_filters( 'eventkoi_get_calendar_count', $count, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:139`
- Lite: `includes/core/class-calendar.php:131`

#### `eventkoi_get_calendar_day_start_time`

_Pro + Lite · filter_

Filters the calendar's `day_start_time` value returned by `Calendar::get_day_start_time()`.

**Fires:** On every call to `Calendar::get_day_start_time()`.

```php
apply_filters( 'eventkoi_get_calendar_day_start_time', $start_time, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:247`
- Lite: `includes/core/class-calendar.php:239`

#### `eventkoi_get_calendar_default_month`

_Pro + Lite · filter_

Filters the calendar's `default_month` value returned by `Calendar::get_default_month()`.

**Fires:** On every call to `Calendar::get_default_month()`.

```php
apply_filters( 'eventkoi_get_calendar_default_month', $month, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:162`
- Lite: `includes/core/class-calendar.php:154`

#### `eventkoi_get_calendar_default_year`

_Pro + Lite · filter_

Filters the calendar's `default_year` value returned by `Calendar::get_default_year()`.

**Fires:** On every call to `Calendar::get_default_year()`.

```php
apply_filters( 'eventkoi_get_calendar_default_year', $year, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:185`
- Lite: `includes/core/class-calendar.php:177`

#### `eventkoi_get_calendar_display`

_Pro + Lite · filter_

Filters the calendar's `display` value returned by `Calendar::get_display()`.

**Fires:** On every call to `Calendar::get_display()`.

```php
apply_filters( 'eventkoi_get_calendar_display', $display, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:198`
- Lite: `includes/core/class-calendar.php:190`

#### `eventkoi_get_calendar_id`

_Pro + Lite · filter_

Filters the calendar's `id` value returned by `Calendar::get_id()`.

**Fires:** On every call to `Calendar::get_id()`.

```php
apply_filters( 'eventkoi_get_calendar_id', $id, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:99`
- Lite: `includes/core/class-calendar.php:91`

#### `eventkoi_get_calendar_list_date_end`

_Pro only · filter_

Filters the calendar's `list_date_end` value returned by `Calendar::get_list_date_end()`.

**Fires:** On every call to `Calendar::get_list_date_end()`.

```php
apply_filters( 'eventkoi_get_calendar_list_date_end', $date_end, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:371`

#### `eventkoi_get_calendar_list_date_start`

_Pro only · filter_

Filters the calendar's `list_date_start` value returned by `Calendar::get_list_date_start()`.

**Fires:** On every call to `Calendar::get_list_date_start()`.

```php
apply_filters( 'eventkoi_get_calendar_list_date_start', $date_start, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:355`

#### `eventkoi_get_calendar_list_expand_instances`

_Pro only · filter_

Filters the calendar's `list_expand_instances` value returned by `Calendar::get_list_expand_instances()`.

**Fires:** On every call to `Calendar::get_list_expand_instances()`.

```php
apply_filters( 'eventkoi_get_calendar_list_expand_instances', $expand, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:339`

#### `eventkoi_get_calendar_list_load_mode`

_Pro only · filter_

Filters the calendar's `list_load_mode` value returned by `Calendar::get_list_load_mode()`.

**Fires:** On every call to `Calendar::get_list_load_mode()`.

```php
apply_filters( 'eventkoi_get_calendar_list_load_mode', $mode, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:328`

#### `eventkoi_get_calendar_list_max_results`

_Pro only · filter_

Filters the calendar's `list_max_results` value returned by `Calendar::get_list_max_results()`.

**Fires:** On every call to `Calendar::get_list_max_results()`.

```php
apply_filters( 'eventkoi_get_calendar_list_max_results', $max_results, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:312`

#### `eventkoi_get_calendar_list_order`

_Pro only · filter_

Filters the calendar's `list_order` value returned by `Calendar::get_list_order()`.

**Fires:** On every call to `Calendar::get_list_order()`.

```php
apply_filters( 'eventkoi_get_calendar_list_order', $order, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:287`

#### `eventkoi_get_calendar_list_orderby`

_Pro only · filter_

Filters the calendar's `list_orderby` value returned by `Calendar::get_list_orderby()`.

**Fires:** On every call to `Calendar::get_list_orderby()`.

```php
apply_filters( 'eventkoi_get_calendar_list_orderby', $orderby, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:273`

#### `eventkoi_get_calendar_list_per_page`

_Pro only · filter_

Filters the calendar's `list_per_page` value returned by `Calendar::get_list_per_page()`.

**Fires:** On every call to `Calendar::get_list_per_page()`.

```php
apply_filters( 'eventkoi_get_calendar_list_per_page', $per_page, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:301`

#### `eventkoi_get_calendar_meta`

_Pro + Lite · filter_

Filters the calendar's `meta` value returned by `Calendar::get_meta()`.

**Fires:** On every call to `Calendar::get_meta()`.

```php
apply_filters( 'eventkoi_get_calendar_meta', $meta, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:90`
- Lite: `includes/core/class-calendar.php:82`

#### `eventkoi_get_calendar_name`

_Pro + Lite · filter_

Filters the calendar's `name` value returned by `Calendar::get_name()`.

**Fires:** On every call to `Calendar::get_name()`.

```php
apply_filters( 'eventkoi_get_calendar_name', $name, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:108`
- Lite: `includes/core/class-calendar.php:100`

#### `eventkoi_get_calendar_shortcode`

_Pro + Lite · filter_

Filters the calendar's `shortcode` value returned by `Calendar::get_shortcode()`.

**Fires:** On every call to `Calendar::get_shortcode()`.

```php
apply_filters( 'eventkoi_get_calendar_shortcode', $shortcode, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:393`
- Lite: `includes/core/class-calendar.php:261`

#### `eventkoi_get_calendar_slug`

_Pro + Lite · filter_

Filters the calendar's `slug` value returned by `Calendar::get_slug()`.

**Fires:** On every call to `Calendar::get_slug()`.

```php
apply_filters( 'eventkoi_get_calendar_slug', $slug, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:117`
- Lite: `includes/core/class-calendar.php:109`

#### `eventkoi_get_calendar_startday`

_Pro + Lite · filter_

Filters the calendar's `startday` value returned by `Calendar::get_startday()`.

**Fires:** On every call to `Calendar::get_startday()`.

```php
apply_filters( 'eventkoi_get_calendar_startday', $startday, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:231`
- Lite: `includes/core/class-calendar.php:223`

#### `eventkoi_get_calendar_timeframe`

_Pro + Lite · filter_

Filters the calendar's `timeframe` value returned by `Calendar::get_timeframe()`.

**Fires:** On every call to `Calendar::get_timeframe()`.

```php
apply_filters( 'eventkoi_get_calendar_timeframe', $timeframe, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:211`
- Lite: `includes/core/class-calendar.php:203`

#### `eventkoi_get_calendar_url`

_Pro + Lite · filter_

Filters the calendar's `url` value returned by `Calendar::get_url()`.

**Fires:** On every call to `Calendar::get_url()`.

```php
apply_filters( 'eventkoi_get_calendar_url', $url, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:130`
- Lite: `includes/core/class-calendar.php:122`

#### `eventkoi_get_event_calendar`

_Pro + Lite · filter_

Filters the event's `calendar` value returned by `Event::get_calendar()`. Override to change what `calendar` resolves to for a given event.

**Fires:** On every call to `Event::get_calendar()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_calendar', $calendar, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1252`
- Lite: `includes/core/class-event.php:801`

#### `eventkoi_pre_update_calendar_meta`

_Pro + Lite · filter_

Filters the meta array passed into `Calendar::update()` before any fields are persisted. Use to inject computed defaults for new calendars or sanitize incoming values upfront.

**Fires:** Once per calendar create/update.

```php
apply_filters( 'eventkoi_pre_update_calendar_meta', $meta, $meta['id'] );
```

- Pro: `includes/core/class-calendar.php:403`
- Lite: `includes/core/class-calendar.php:271`

#### `eventkoi_rendered_event_calendar`

_Pro + Lite · filter_

Filters the rendered output of the `{event_calendar}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('calendar')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_calendar', implode( ', ', $names ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2963`
- Lite: `includes/core/class-event.php:2092`

#### `eventkoi_rendered_event_calendar_url`

_Pro + Lite · filter_

Filters the rendered output of the `{event_calendar_url}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('calendar_url')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_calendar_url', $url, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2982`
- Lite: `includes/core/class-event.php:2111`

### Actions

#### `eventkoi_after_calendar_content`

_Pro + Lite · action_

Fires inside the single-calendar template, immediately after the calendar markup and `eventkoi_single_calendar_template`, before the footer.

**Fires:** Once per single calendar page render.

```php
do_action( 'eventkoi_after_calendar_content' );
```

- Pro: `templates/single-calendar.php:39`
- Lite: `templates/single-calendar.php:39`

#### `eventkoi_after_update_calendar_meta`

_Pro + Lite · action_

Fires inside `Calendar::update_meta()` after every term meta key has been written. Receives the meta array, calendar ID, and term object.

**Fires:** Once per calendar meta save.

```php
do_action( 'eventkoi_after_update_calendar_meta', $meta, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:532`
- Lite: `includes/core/class-calendar.php:356`

#### `eventkoi_before_calendar_content`

_Pro + Lite · action_

Fires inside the single-calendar template, immediately after the header and before EventKoi renders calendar markup. Use to inject breadcrumbs, banners, or other above-the-fold content.

**Fires:** Once per single calendar (event_cal taxonomy term) page render.

```php
do_action( 'eventkoi_before_calendar_content' );
```

- Pro: `templates/single-calendar.php:34`
- Lite: `templates/single-calendar.php:34`

#### `eventkoi_before_update_calendar_meta`

_Pro + Lite · action_

Fires inside `Calendar::update_meta()` after the incoming meta has been filtered, but before any term meta is written. Receives the filtered meta, calendar ID, and term object.

**Fires:** Once per calendar meta save.

```php
do_action( 'eventkoi_before_update_calendar_meta', $meta, self::$calendar_id, self::$calendar );
```

- Pro: `includes/core/class-calendar.php:468`
- Lite: `includes/core/class-calendar.php:336`

#### `eventkoi_single_calendar_template`

_Pro + Lite · action_

Fires inside the single-calendar template right after the calendar content is echoed. Hook this to append related content (Upcoming events list, share buttons, etc.) within the same wrapper.

**Fires:** Once per single calendar page render.

```php
do_action( 'eventkoi_single_calendar_template' );
```

- Pro: `templates/single-calendar.php:37`
- Lite: `templates/single-calendar.php:37`

## RSVPs

### Filters

#### `eventkoi_get_event_rsvp_allow_edit`

_Pro + Lite · filter_

Filters the event's `rsvp_allow_edit` value returned by `Event::get_rsvp_allow_edit()`. Override to change what `rsvp_allow_edit` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_allow_edit()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_allow_edit', (bool) $allow_edit, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2380`
- Lite: `includes/core/class-event.php:1668`

#### `eventkoi_get_event_rsvp_allow_guests`

_Pro + Lite · filter_

Filters the event's `rsvp_allow_guests` value returned by `Event::get_rsvp_allow_guests()`. Override to change what `rsvp_allow_guests` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_allow_guests()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_allow_guests', (bool) $allow_guests, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2353`
- Lite: `includes/core/class-event.php:1641`

#### `eventkoi_get_event_rsvp_auto_account`

_Pro + Lite · filter_

Filters the event's `rsvp_auto_account` value returned by `Event::get_rsvp_auto_account()`. Override to change what `rsvp_auto_account` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_auto_account()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_auto_account', (bool) $auto_account, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2391`
- Lite: `includes/core/class-event.php:1679`

#### `eventkoi_get_event_rsvp_capacity`

_Pro + Lite · filter_

Filters the event's `rsvp_capacity` value returned by `Event::get_rsvp_capacity()`. Override to change what `rsvp_capacity` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_capacity()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_capacity', $capacity, self::$event_id, self::$event, $instance_ts );
```

- Pro: `includes/core/class-event.php:2326`
- Lite: `includes/core/class-event.php:1616`

#### `eventkoi_get_event_rsvp_enabled`

_Pro + Lite · filter_

Filters the event's `rsvp_enabled` value returned by `Event::get_rsvp_enabled()`. Override to change what `rsvp_enabled` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_enabled()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_enabled', (bool) $enabled, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2302`
- Lite: `includes/core/class-event.php:1602`

#### `eventkoi_get_event_rsvp_max_guests`

_Pro + Lite · filter_

Filters the event's `rsvp_max_guests` value returned by `Event::get_rsvp_max_guests()`. Override to change what `rsvp_max_guests` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_max_guests()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_max_guests', absint( $max_guests ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2364`
- Lite: `includes/core/class-event.php:1652`

#### `eventkoi_get_event_rsvp_sale_end`

_Pro + Lite · filter_

Filters the event's `rsvp_sale_end` value returned by `Event::get_rsvp_sale_end()`. Override to change what `rsvp_sale_end` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_sale_end()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_sale_end', $end, self::$event_id, self::$event, $instance_ts );
```

- Pro: `includes/core/class-event.php:2436`
- Lite: `includes/core/class-event.php:1706`

#### `eventkoi_get_event_rsvp_sale_start`

_Pro + Lite · filter_

Filters the event's `rsvp_sale_start` value returned by `Event::get_rsvp_sale_start()`. Override to change what `rsvp_sale_start` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_sale_start()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_sale_start', $start, self::$event_id, self::$event, $instance_ts );
```

- Pro: `includes/core/class-event.php:2414`
- Lite: `includes/core/class-event.php:1694`

#### `eventkoi_get_event_rsvp_show_remaining`

_Pro + Lite · filter_

Filters the event's `rsvp_show_remaining` value returned by `Event::get_rsvp_show_remaining()`. Override to change what `rsvp_show_remaining` resolves to for a given event.

**Fires:** On every call to `Event::get_rsvp_show_remaining()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_rsvp_show_remaining', (bool) $show_remaining, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2342`
- Lite: `includes/core/class-event.php:1630`

#### `eventkoi_rendered_event_rsvp`

_Pro + Lite · filter_

Filters the rendered output of the `{event_rsvp}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('rsvp')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_rsvp', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3139`
- Lite: `includes/core/class-event.php:2268`

#### `eventkoi_rendered_event_rsvp_capacity`

_Pro + Lite · filter_

Filters the rendered RSVP capacity string emitted by the `{event_rsvp_capacity}` dynamic tag (empty when capacity is unlimited).

**Fires:** When the dynamic tag is rendered in templates, blocks, or shortcodes.

```php
apply_filters( 'eventkoi_rendered_event_rsvp_capacity', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4216`
- Lite: `includes/core/class-event.php:3261`

#### `eventkoi_rendered_event_rsvp_full`

_Pro + Lite · filter_

Filters the rendered 'RSVP full' label that's emitted when capacity is reached. Empty when not full.

**Fires:** When the dynamic tag is rendered.

```php
apply_filters( 'eventkoi_rendered_event_rsvp_full', $label, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4249`
- Lite: `includes/core/class-event.php:3294`

#### `eventkoi_rendered_event_rsvp_going`

_Pro + Lite · filter_

Filters the rendered count of attendees marked 'going'.

**Fires:** When the dynamic tag is rendered.

```php
apply_filters( 'eventkoi_rendered_event_rsvp_going', (string) $snap['going'], self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4237`
- Lite: `includes/core/class-event.php:3282`

#### `eventkoi_rendered_event_rsvp_remaining`

_Pro + Lite · filter_

Filters the rendered remaining-RSVP-spots string. Empty when capacity is unlimited.

**Fires:** When the dynamic tag is rendered.

```php
apply_filters( 'eventkoi_rendered_event_rsvp_remaining', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4227`
- Lite: `includes/core/class-event.php:3272`

#### `eventkoi_rsvp_email_subject`

_Pro + Lite · filter_

Filters the subject of the RSVP confirmation email before tag replacement.

**Fires:** Right before `wp_mail()` for an RSVP confirmation.

```php
apply_filters( 'eventkoi_rsvp_email_subject', $subject, $tags, $event_id, $instance_ts );
```

- Pro: `includes/core/class-rsvps.php:1083`
- Lite: `includes/core/class-rsvps.php:970`

#### `eventkoi_rsvp_email_tags`

_Pro + Lite · filter_

Filters the `[tag] => value` replacements available inside the RSVP confirmation email template.

**Fires:** Once per RSVP-confirmation render.

```php
apply_filters( 'eventkoi_rsvp_email_tags', $tags, $event_id, $instance_ts );
```

- Pro: `includes/core/class-rsvps.php:1035`
- Lite: `includes/core/class-rsvps.php:925`

#### `eventkoi_rsvp_email_template`

_Pro + Lite · filter_

Filters the body template of the RSVP confirmation email. The default Hooks handler returns the value saved in settings when non-empty, otherwise the dynamic default that adapts to the Allow-RSVP-edits toggle.

**Fires:** Right before tag replacement, on every RSVP-confirmation send.

```php
apply_filters( 'eventkoi_rsvp_email_template', $default_body, $tags, $event_id, $instance_ts );
```

- Pro: `includes/core/class-rsvps.php:1066`
- Lite: `includes/core/class-rsvps.php:953`

#### `eventkoi_rsvp_qr_code`

_Pro only · filter_

Filters the rendered `<img>` tag for the RSVP QR code.

**Fires:** When the RSVP email is being assembled.

```php
apply_filters( 'eventkoi_rsvp_qr_code', $qr_code, $qr_url, $checkin_url, $token, $event_id, $instance_ts );
```

- Pro: `includes/core/class-rsvps.php:958`

#### `eventkoi_rsvp_qr_url`

_Pro only · filter_

Filters the QR-code image URL embedded in the RSVP confirmation email. Default points at api.qrserver.com.

**Fires:** When the RSVP email is being assembled.

```php
apply_filters( 'eventkoi_rsvp_qr_url', $qr_url, $checkin_url, $token, $event_id, $instance_ts );
```

- Pro: `includes/core/class-rsvps.php:952`

## Tickets and orders

### Filters

#### `eventkoi_get_event_tickets_display_mode`

_Pro + Lite · filter_

Filters the event's `tickets_display_mode` value returned by `Event::get_tickets_display_mode()`. Override to change what `tickets_display_mode` resolves to for a given event.

**Fires:** On every call to `Event::get_tickets_display_mode()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_tickets_display_mode', $mode, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2559`
- Lite: `includes/core/class-event.php:1591`

#### `eventkoi_get_event_tickets_enabled`

_Pro + Lite · filter_

Filters the event's `tickets_enabled` value returned by `Event::get_tickets_enabled()`. Override to change what `tickets_enabled` resolves to for a given event.

**Fires:** On every call to `Event::get_tickets_enabled()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_tickets_enabled', (bool) $enabled, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2486`
- Lite: `includes/core/class-event.php:1519`

#### `eventkoi_get_event_tickets_terms_conditions`

_Pro + Lite · filter_

Filters the event's `tickets_terms_conditions` value returned by `Event::get_tickets_terms_conditions()`. Override to change what `tickets_terms_conditions` resolves to for a given event.

**Fires:** On every call to `Event::get_tickets_terms_conditions()` — so anywhere the editor, REST API, blocks, shortcodes, or page builders read this field.

```php
apply_filters( 'eventkoi_get_event_tickets_terms_conditions', $terms, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2497`
- Lite: `includes/core/class-event.php:1530`

#### `eventkoi_rendered_event_ticket_count`

_Pro + Lite · filter_

Filters the rendered output of the `{event_ticket_count}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('ticket_count')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_ticket_count', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3833`
- Lite: `includes/core/class-event.php:2926`

#### `eventkoi_rendered_event_ticket_price_from`

_Pro + Lite · filter_

Filters the rendered output of the `{event_ticket_price_from}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('ticket_price_from')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_ticket_price_from', $out, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3991`
- Lite: `includes/core/class-event.php:3071`

#### `eventkoi_rendered_event_ticket_price_range`

_Pro + Lite · filter_

Filters the rendered output of the `{event_ticket_price_range}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('ticket_price_range')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_ticket_price_range', '', self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4020`
- Lite: `includes/core/class-event.php:3100`

#### `eventkoi_rendered_event_ticket_price_to`

_Pro + Lite · filter_

Filters the rendered output of the `{event_ticket_price_to}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('ticket_price_to')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_ticket_price_to', '', self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:4002`
- Lite: `includes/core/class-event.php:3082`

#### `eventkoi_rendered_event_ticket_summary`

_Pro + Lite · filter_

Filters the rendered output of the `{event_ticket_summary}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('ticket_summary')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_ticket_summary', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3851`
- Lite: `includes/core/class-event.php:2944`

#### `eventkoi_rendered_event_tickets`

_Pro + Lite · filter_

Filters the rendered output of the `{event_tickets}` dynamic tag — i.e. the formatted string visitors see when this token is used in templates, blocks, or shortcodes.

**Fires:** When `Event::render_meta('tickets')` resolves, on every consumer that uses dynamic tags.

```php
apply_filters( 'eventkoi_rendered_event_tickets', $output, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:3134`
- Lite: `includes/core/class-event.php:2263`

#### `eventkoi_ticket_email_subject`

_Pro + Lite · filter_

Filters the subject line of the ticket confirmation email before tag replacement and sending.

**Fires:** Right before `wp_mail()` for a ticket confirmation.

```php
apply_filters( 'eventkoi_ticket_email_subject', $subject_default, $tags, $order, $items );
```

- Pro: `includes/core/class-ticket-emails.php:363`
- Lite: `includes/core/class-ticket-emails.php:337`

#### `eventkoi_ticket_email_tags`

_Pro + Lite · filter_

Filters the array of `[tag] => value` replacements available inside the ticket confirmation email template.

**Fires:** Once per ticket-confirmation render.

```php
apply_filters( 'eventkoi_ticket_email_tags', $tags, $order, $items );
```

- Pro: `includes/core/class-ticket-emails.php:360`
- Lite: `includes/core/class-ticket-emails.php:334`

#### `eventkoi_ticket_email_template`

_Pro + Lite · filter_

Filters the body template of the ticket confirmation email before tag replacement. Returning a non-empty string overrides the default body wholesale.

**Fires:** Right before tag replacement, on every ticket-confirmation send.

```php
apply_filters( 'eventkoi_ticket_email_template', $default_body, $tags, $order, $items );
```

- Pro: `includes/core/class-ticket-emails.php:383`
- Lite: `includes/core/class-ticket-emails.php:356`

#### `eventkoi_ticket_qr_url`

_Pro only · filter_

Filters the URL of the QR-code image embedded in per-ticket (individual seat) confirmation rows. Receives `($qr_url, $checkin_url, $checkin_code, $event_id, $instance_ts)`.

**Fires:** Once per ticket QR generation, inside the ticket-emails assembler.

```php
apply_filters( 'eventkoi_ticket_qr_url', $qr_url, $checkin_url, $checkin_code, $event_id, $instance_ts );
```

- Pro: `includes/core/class-ticket-emails.php:330`

## Blocks and shortcodes

### Filters

#### `eventkoi_block_live_stripe_on_staging`

_Pro only · filter_

Filters whether EventKoi refuses live-mode Stripe Connect on a staging or local URL. Default is `true`. Override to `false` only if you're running a genuine production install behind a non-public domain.

**Fires:** Per call to the Stripe Connect bootstrap.

```php
apply_filters( 'eventkoi_block_live_stripe_on_staging', true )
		) {
			return new \WP_Error(
				'eventkoi_stripe_live_on_staging',
				__( 'Live-mode Stripe keys cannot be connected on staging or local URLs. Use test-mode keys here.', 'eventkoi' ) );
```

- Pro: `includes/payments/class-stripe.php:742`

## Page builders and loops

### Filters

#### `eventkoi_beaver_route_occurrence_query`

_Pro only · filter_

Filters whether EventKoi should rewrite the current Beaver Builder loop query to use occurrence-aware matching. Receives `($enabled, $args, $temporal, $orders_by_temporal)`.

**Fires:** Once per BB loop module render that targets EventKoi events.

```php
apply_filters( 'eventkoi_beaver_route_occurrence_query', ( $has_temporal_filter || $orders_by_temporal || $instance_mode ), $args, $temporal, $orders_by_temporal );
```

- Pro: `includes/core/class-beaver-loop-query.php:144`

#### `eventkoi_loop_default_window_seconds`

_Pro only · filter_

Filters the default future window (in seconds) used when expanding recurring instances inside a Beaver Builder loop with no explicit date range. Default 12 months.

**Fires:** Inside the BB loop expansion path when `from`/`to` are missing.

```php
apply_filters( 'eventkoi_loop_default_window_seconds', YEAR_IN_SECONDS );
```

- Pro: `includes/core/class-beaver-loop-query.php:182`

## Admin and UI

### Filters

#### `eventkoi_admin_menu_items`

_Pro + Lite · filter_

Filters the array of items rendered as sub-pages under the EventKoi admin menu. Add an entry to expose a custom React route.

**Fires:** Once per admin menu render.

```php
apply_filters( 'eventkoi_admin_menu_items', array(
				'dashboard' => __( 'Dashboard', 'eventkoi' ),
				'events'    => __( 'Events', 'eventkoi' ),
				'calendars' => __( 'Calendars', 'eventkoi' ),
				'tickets'   => __( 'Ticket sales', 'eventkoi' ),
				'settings'  => __( 'Settings', 'eventkoi' ),
			) );
```

- Pro: `includes/admin/class-menus.php:119`
- Lite: `includes/admin/class-menus.php:148`

#### `eventkoi_admin_params`

_Pro + Lite · filter_

Filters the `eventkoi_params` JS object localized into the admin page. Use to expose extra config to a custom React component or block extension.

**Fires:** Once per admin-screen render that enqueues the EventKoi admin bundle.

```php
apply_filters( 'eventkoi_admin_params', $eventkoi_params ) );
```

- Pro: `includes/admin/class-scripts.php:187`
- Lite: `includes/admin/class-scripts.php:252`

### Actions

#### `eventkoi_admin_installed`

_Pro + Lite · action_

Fires once after `eventkoi_installed` on the same install run. Reserved for admin-only setup that depends on the install having completed (e.g. seeding admin notices, pointers).

**Fires:** Right after `eventkoi_installed` in the install bootstrap.

```php
do_action( 'eventkoi_admin_installed' );
```

- Pro: `includes/core/class-install.php:78`
- Lite: `includes/core/class-install.php:78`

## Other

### Filters

#### `eventkoi_`

_Pro + Lite · filter_

Dynamic filter pattern — actually fires as `eventkoi_<field>_output` for every dynamic tag rendered through `Event::render_meta()`. Receives `($value, $event_id)`. Use to hook a single field-specific filter (e.g. `eventkoi_title_output`) without subscribing to the whole rendering pipeline.

**Fires:** Per dynamic-tag render in templates, blocks, and shortcodes.

```php
apply_filters( 'eventkoi_', . $name . '_output', self::$method(), self::get_id() );
```

- Pro: `includes/core/class-event.php:276`
- Lite: `includes/core/class-event.php:258`

#### `eventkoi_currency`

_Pro + Lite · filter_

Filters the lower-cased ISO currency code used by the stats engine. Override to force stats into a different currency than what's stored in plugin settings.

**Fires:** Once per `Stats` instantiation.

```php
apply_filters( 'eventkoi_currency', strtolower( $currency ) );
```

- Pro: `includes/core/class-stats.php:47`
- Lite: `includes/core/class-stats.php:42`

#### `eventkoi_currency_locale`

_Pro + Lite · filter_

Filters the BCP-47 locale used to format currency values for an individual order/charge result row. Receives `($locale, $row)`.

**Fires:** Per-row during stats / order list assembly.

```php
apply_filters( 'eventkoi_currency_locale', $locale, $results[ $key ] );
```

- Pro: `includes/core/class-hooks.php:306`
- Lite: `includes/core/class-hooks.php:239`

#### `eventkoi_current_theme_support`

_Pro + Lite · filter_

Filters the boolean detection result for whether the active theme supports the block editor / FSE.

**Fires:** Wherever EventKoi needs to decide between block-theme and classic rendering paths.

```php
apply_filters( 'eventkoi_current_theme_support', $support );
```

- Pro: `includes/core/core-functions.php:633`
- Lite: `includes/core/core-functions.php:563`

#### `eventkoi_field_date_format`

_Pro + Lite · filter_

Filters the date format used for a specific field name (e.g. `created`, `last_updated`). Receives `($format, $field)`.

**Fires:** Once per call to `eventkoi_get_field_date_format( $field )`.

```php
apply_filters( 'eventkoi_field_date_format', $format, $field );
```

- Pro: `includes/core/core-functions.php:1020`
- Lite: `includes/core/core-functions.php:908`

#### `eventkoi_frontend_params`

_Pro + Lite · filter_

Filters the `eventkoi_params` JS object localized into frontend pages where EventKoi assets are enqueued. Use to expose extra config to a custom block or shortcode.

**Fires:** Once per frontend request that enqueues the EventKoi frontend bundle.

```php
apply_filters( 'eventkoi_frontend_params', $params ) );
```

- Pro: `includes/core/class-scripts.php:152`
- Lite: `includes/core/class-scripts.php:145`

#### `eventkoi_get_content`

_Pro + Lite · filter_

Filters the raw `wp_template` post content used as the default event template wrapper before `do_blocks()` runs. Override to swap the entire template body in for a specific request.

**Fires:** Once per single-event render that uses a custom default template.

```php
apply_filters( 'eventkoi_get_content', $default_template->post_content ) );
```

- Pro: `includes/core/core-functions.php:339`
- Lite: `includes/core/core-functions.php:306`

#### `eventkoi_get_custom_fields`

_Pro only · filter_

Filters the array of custom field values resolved for an event (keyed by field slug → value).

**Fires:** Once per call to `Event::get_custom_fields()`.

```php
apply_filters( 'eventkoi_get_custom_fields', $fields, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1959`

#### `eventkoi_get_custom_fields_layout`

_Pro only · filter_

Filters the custom-fields layout array (the editor's group/field ordering) returned by `Event::get_custom_fields_layout()`. Returning `null` makes the editor fall back to the global default.

**Fires:** Once per call to `Event::get_custom_fields_layout()`.

```php
apply_filters( 'eventkoi_get_custom_fields_layout', null, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1114`

#### `eventkoi_get_custom_fields_state`

_Pro only · filter_

Filters the custom-fields UI state (collapsed groups, etc.) returned by `Event::get_custom_fields_state()`.

**Fires:** Once per call to `Event::get_custom_fields_state()`.

```php
apply_filters( 'eventkoi_get_custom_fields_state', null, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1133`

#### `eventkoi_get_default_date_format`

_Pro + Lite · filter_

Filters the default PHP date format used by EventKoi when no field-specific override is in play.

**Fires:** Once per call to `eventkoi_get_default_date_format()`.

```php
apply_filters( 'eventkoi_get_default_date_format', $date_format );
```

- Pro: `includes/core/core-functions.php:659`
- Lite: `includes/core/core-functions.php:589`

#### `eventkoi_get_default_template`

_Pro + Lite · filter_

Filters the rendered HTML produced by the legacy `event.php` template fallback. Last chance to mutate the markup before it's output.

**Fires:** From `Blocks::get_default_template()` after rendering the include.

```php
apply_filters( 'eventkoi_get_default_template', $content );
```

- Pro: `includes/core/class-blocks.php:2303`
- Lite: `includes/core/class-blocks.php:1888`

#### `eventkoi_get_end_date_g`

_Pro + Lite · filter_

Filters the Google Calendar-formatted event end datetime returned by `Event::get_end_date_g()`.

**Fires:** Once per call.

```php
apply_filters( 'eventkoi_get_end_date_g', eventkoi_format_gcal_datetime( $raw ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1536`
- Lite: `includes/core/class-event.php:1068`

#### `eventkoi_get_footer`

_Pro + Lite · filter_

Filters the block-template-part markup used as the footer in EventKoi's standalone single-event/calendar templates.

**Fires:** Once per render of a standalone EventKoi template.

```php
apply_filters( 'eventkoi_get_footer', $content ) );
```

- Pro: `includes/core/core-functions.php:323`
- Lite: `includes/core/core-functions.php:288`

#### `eventkoi_get_header`

_Pro + Lite · filter_

Filters the block-template-part markup used as the header in EventKoi's standalone single-event/calendar templates.

**Fires:** Once per render of a standalone EventKoi template.

```php
apply_filters( 'eventkoi_get_header', $content ) );
```

- Pro: `includes/core/core-functions.php:300`
- Lite: `includes/core/core-functions.php:265`

#### `eventkoi_get_order_stats`

_Pro + Lite · filter_

Filters the assembled overall stats array returned by `Stats::get()` (total_orders, total_earnings, tickets_sold, total_refunded).

**Fires:** On every call to `Stats::get()`.

```php
apply_filters( 'eventkoi_get_order_stats', $stats );
```

- Pro: `includes/core/class-stats.php:63`
- Lite: `includes/core/class-stats.php:58`

#### `eventkoi_get_private_api_key`

_Pro + Lite · filter_

Filters the private REST API key returned by `REST::get_api_key()` (after sanitization). Override to inject a token from a secrets manager.

**Fires:** Whenever the editor or REST permission callback reads the API key.

```php
apply_filters( 'eventkoi_get_private_api_key', esc_attr( $api_key ) );
```

- Pro: `includes/api/class-rest.php:167`
- Lite: `includes/api/class-rest.php:159`

#### `eventkoi_get_settings`

_Pro + Lite · filter_

Filters the merged settings array returned by `Settings::get()` (includes license fields read from dedicated options).

**Fires:** On every call to `Settings::get()`.

```php
apply_filters( 'eventkoi_get_settings', $settings );
```

- Pro: `includes/core/class-settings.php:44`
- Lite: `includes/core/class-settings.php:35`

#### `eventkoi_get_start_date_g`

_Pro + Lite · filter_

Filters the Google Calendar-formatted event start datetime (e.g. `20250327T160300+0400`) returned by `Event::get_start_date_g()`.

**Fires:** Once per call.

```php
apply_filters( 'eventkoi_get_start_date_g', eventkoi_format_gcal_datetime( $raw ), self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:1521`
- Lite: `includes/core/class-event.php:1053`

#### `eventkoi_get_status_title`

_Pro + Lite · filter_

Filters the human-readable status label produced by `eventkoi_get_status_title()`. Receives `($label, $status)`.

**Fires:** Whenever a status is rendered for display.

```php
apply_filters( 'eventkoi_get_status_title', $label, $status );
```

- Pro: `includes/core/core-functions.php:876`
- Lite: `includes/core/core-functions.php:806`

#### `eventkoi_get_stripe_currency`

_Pro only · filter_

Filters the lowercase currency code returned by `Stripe::get_currency()` (default `usd`).

**Fires:** Once per Stripe currency lookup.

```php
apply_filters( 'eventkoi_get_stripe_currency', $currency );
```

- Pro: `includes/payments/class-stripe.php:934`

#### `eventkoi_get_stripe_webhook_secret`

_Pro + Lite · filter_

Filters the resolved Stripe webhook signing secret. Use to source the secret from a vault instead of plugin settings.

**Fires:** Once per Stripe webhook delivery.

```php
apply_filters( 'eventkoi_get_stripe_webhook_secret', $webhook_secret );
```

- Pro: `includes/core/core-functions.php:918`
- Lite: `includes/core/core-functions.php:1233`

#### `eventkoi_get_template_asset`

_Pro + Lite · filter_

Filters the resolved URL of an asset under `templates/assets/`. Override to serve assets from a CDN.

**Fires:** Whenever a template asset is referenced.

```php
apply_filters( 'eventkoi_get_template_asset', $url, $asset );
```

- Pro: `includes/core/core-functions.php:277`
- Lite: `includes/core/core-functions.php:242`

#### `eventkoi_get_timezone_display`

_Pro + Lite · filter_

Filters whether the timezone label should be displayed on the event page. Default comes from the per-event `timezone_display` post meta.

**Fires:** Once per call to `Event::get_timezone_display()`.

```php
apply_filters( 'eventkoi_get_timezone_display', (bool) $timezone_display, self::$event_id, self::$event );
```

- Pro: `includes/core/class-event.php:2093`
- Lite: `includes/core/class-event.php:1238`

#### `eventkoi_live_mode_enabled`

_Pro + Lite · filter_

Filters whether EventKoi considers itself in live mode. Default comes from plugin settings.

**Fires:** Once per call to `eventkoi_live_mode_enabled()`.

```php
apply_filters( 'eventkoi_live_mode_enabled', $live );
```

- Pro: `includes/core/core-functions.php:935`
- Lite: `includes/core/core-functions.php:823`

#### `eventkoi_locate_template`

_Pro + Lite · filter_

Filters the filesystem path returned by `eventkoi_locate_template()`. Use to swap any plugin template for a theme override before the default `eventkoi/` directory lookup completes.

**Fires:** Whenever EventKoi loads a template part.

```php
apply_filters( 'eventkoi_locate_template', $template, $template_name, $default_path );
```

- Pro: `includes/core/core-functions.php:1174`
- Lite: `includes/core/core-functions.php:1062`

#### `eventkoi_login_url`

_Pro only · filter_

Filters the login URL EventKoi uses for redirects (RSVP edit links, QR check-in, etc.). Default is `wp_login_url()`.

**Fires:** Whenever EventKoi assembles a frontend login URL.

```php
apply_filters( 'eventkoi_login_url', wp_login_url() ), );
```

- Pro: `includes/core/class-scripts.php:143`

#### `eventkoi_low_stock_threshold`

_Pro + Lite · filter_

Filters the threshold below which an event's remaining inventory is treated as 'low stock'. Default is `max(5, ceil(capacity * 0.1))`. Receives `($threshold, $event_id, $capacity)`.

**Fires:** Once per `{event_low_stock}` dynamic tag render with capacity > 0.

```php
apply_filters( 'eventkoi_low_stock_threshold', $default_threshold, self::$event_id, $snap['capacity'] );
```

- Pro: `includes/core/class-event.php:3817`
- Lite: `includes/core/class-event.php:2910`

#### `eventkoi_max_recurrence_iterations`

_Pro + Lite · filter_

Filters the maximum number of occurrences EventKoi will iterate for any single recurrence rule. Default 500. Floored at 50.

**Fires:** When expanding recurring rules into instance rows.

```php
apply_filters( 'eventkoi_max_recurrence_iterations', 500 );
```

- Pro: `includes/core/class-beaver-loop-query.php:1781`
- Lite: `includes/core/class-event.php:3635`

#### `eventkoi_max_upload_size_mb`

_Pro + Lite · filter_

Filters the maximum upload size (in MB) the EventKoi REST upload handler will accept for event/calendar images. Default 5.

**Fires:** On every call to the upload REST endpoint.

```php
apply_filters( 'eventkoi_max_upload_size_mb', 5 );
```

- Pro: `includes/api/class-uploads.php:115`
- Lite: `includes/api/class-uploads.php:122`

#### `eventkoi_pre_setting_value`

_Pro + Lite · filter_

Filters each individual sanitized setting value before it's stored on the in-memory settings array. Receives `($sanitized, $key)`.

**Fires:** Per-key during a save through the REST settings endpoint.

```php
apply_filters( 'eventkoi_pre_setting_value', $sanitized, $key );
```

- Pro: `includes/api/class-settings.php:170`
- Lite: `includes/api/class-settings.php:174`

#### `eventkoi_prepare_raw_db_data`

_Pro + Lite · filter_

Filters raw database rows returned by REST endpoints (orders, RSVPs, etc.) to allow consumer-side reshaping. Receives the rows array and a string identifying the dataset.

**Fires:** Whenever a private REST endpoint serializes raw rows.

```php
apply_filters( 'eventkoi_prepare_raw_db_data', array( (object) $data ), 'order' );
```

- Pro: `includes/api/class-order.php:71`
- Lite: `includes/api/class-order.php:73`

#### `eventkoi_qr_checkin_capability`

_Pro only · filter_

Filters the WordPress capability required to perform a QR check-in. Default `manage_options`. Lower it (e.g. `edit_posts`) to let front-of-house staff scan attendees.

**Fires:** On every QR check-in attempt.

```php
apply_filters( 'eventkoi_qr_checkin_capability', 'manage_options' );
```

- Pro: `includes/core/class-qr-checkin.php:77`

#### `eventkoi_raw_client_ip`

_Pro + Lite · filter_

Filters the sanitized client IP returned by EventKoi's IP detector (used by the rate limiter and audit logs).

**Fires:** Once per call to `Rate_Limiter::get_client_ip()`.

```php
apply_filters( 'eventkoi_raw_client_ip', $raw_ip );
```

- Pro: `includes/core/core-functions.php:993`
- Lite: `includes/core/core-functions.php:881`

#### `eventkoi_refund_email_subject`

_Pro + Lite · filter_

Filters the subject line of the refund-confirmation email.

**Fires:** Right before `wp_mail()` for a refund notification.

```php
apply_filters( 'eventkoi_refund_email_subject', $subject_raw, $tags, $order );
```

- Pro: `includes/core/class-ticket-emails.php:512`
- Lite: `includes/core/class-ticket-emails.php:479`

#### `eventkoi_refund_email_tags`

_Pro + Lite · filter_

Filters the tag replacements available inside the refund-confirmation email template.

**Fires:** Once per refund-confirmation render.

```php
apply_filters( 'eventkoi_refund_email_tags', $tags, $order, $refund_items );
```

- Pro: `includes/core/class-ticket-emails.php:506`
- Lite: `includes/core/class-ticket-emails.php:473`

#### `eventkoi_refund_email_template`

_Pro + Lite · filter_

Filters the body template of the refund-confirmation email.

**Fires:** Right before tag replacement, on every refund-confirmation send.

```php
apply_filters( 'eventkoi_refund_email_template', $body, $tags, $order );
```

- Pro: `includes/core/class-ticket-emails.php:534`
- Lite: `includes/core/class-ticket-emails.php:501`

#### `eventkoi_rendered_custom_field`

_Pro only · filter_

Filters the rendered HTML for a single custom field on an event. Receives `($value, $field_key, $event_id, $event)`.

**Fires:** Per custom field render in the event template / blocks.

```php
apply_filters( 'eventkoi_rendered_custom_field', $value, $field_key, self::$event_id, $show_label );
```

- Pro: `includes/core/class-event.php:319`

#### `eventkoi_rendered_custom_field_group`

_Pro only · filter_

Filters the rendered HTML for a custom-field group container. Receives `($output, $group_key, $event_id, $show_labels)`.

**Fires:** Per custom-field group render.

```php
apply_filters( 'eventkoi_rendered_custom_field_group', $output, $group_key, self::$event_id, $show_labels );
```

- Pro: `includes/core/class-event.php:393`

#### `eventkoi_rendered_custom_fields`

_Pro only · filter_

Filters the assembled HTML for the entire custom-fields container rendered by the `{event_custom_fields}` dynamic tag.

**Fires:** Per custom-fields container render.

```php
apply_filters( 'eventkoi_rendered_custom_fields', $output, self::$event_id );
```

- Pro: `includes/core/class-event.php:514`

#### `eventkoi_rendered_meta_for_`

_Pro + Lite · filter_

Dynamic filter — actually fires as `eventkoi_rendered_meta_for_<key>` for each key the renderer doesn't have a dedicated `rendered_<key>` method for. Use to add support for custom dynamic tags. Receives `($value, $event_id)`.

**Fires:** Per dynamic-tag render that falls through the default branch.

```php
apply_filters( 'eventkoi_rendered_meta_for_', . $key, $value, self::$event_id );
```

- Pro: `includes/core/class-event.php:521`
- Lite: `includes/core/class-event.php:279`

#### `eventkoi_set_settings`

_Pro + Lite · filter_

Filters the sanitized settings array immediately before it's written to the `eventkoi_settings` option. Use to inject defaults or strip keys you don't want persisted.

**Fires:** On every settings save, after sanitization.

```php
apply_filters( 'eventkoi_set_settings', $settings ) );
```

- Pro: `includes/core/class-settings.php:96`
- Lite: `includes/core/class-settings.php:49`

#### `eventkoi_timezone`

_Pro + Lite · filter_

Filters the timezone string returned by `eventkoi_timezone()` (falls back to a synthesized `UTC±H[:MM]` when no IANA name is available).

**Fires:** Once per call to `eventkoi_timezone()`.

```php
apply_filters( 'eventkoi_timezone', $timezone );
```

- Pro: `includes/core/core-functions.php:780`
- Lite: `includes/core/core-functions.php:710`

### Actions

#### `eventkoi_after_order_created`

_Pro + Lite · action_

Fires after a new ticket order has been created on the configured gateway. Receives the args passed in and the gateway slug (`stripe`, `woocommerce`).

**Fires:** Once per `Orders::create_order()` call.

```php
do_action( 'eventkoi_after_order_created', $args, $gateway );
```

- Pro: `includes/core/class-orders.php:44`
- Lite: `includes/core/class-orders.php:39`

#### `eventkoi_after_order_updated`

_Pro + Lite · action_

Fires after a charge row in `wp_eventkoi_charges` has been upserted by `Order::update()`. Receives the upserted args and gateway slug.

**Fires:** Whenever a webhook or admin action mutates a charge row.

```php
do_action( 'eventkoi_after_order_updated', $args, $gateway );
```

- Pro: `includes/core/class-order.php:120`
- Lite: `includes/core/class-order.php:120`

#### `eventkoi_after_register_post_type`

_Pro + Lite · action_

Fires immediately after the `eventkoi_event` post type is registered.

**Fires:** Once per request, after `register_post_type()` returns.

```php
do_action( 'eventkoi_after_register_post_type' );
```

- Pro: `includes/core/class-post-types.php:162`
- Lite: `includes/core/class-post-types.php:162`

#### `eventkoi_after_register_taxonomy`

_Pro + Lite · action_

Fires immediately after the `event_cal` taxonomy is registered.

**Fires:** Once per request, after `register_taxonomy()` returns.

```php
do_action( 'eventkoi_after_register_taxonomy' );
```

- Pro: `includes/core/class-post-types.php:84`
- Lite: `includes/core/class-post-types.php:84`

#### `eventkoi_before_save_settings`

_Pro + Lite · action_

Fires inside `Settings::set()` before the incoming settings array is sanitized and persisted. Receives the raw settings array. Use to audit-log changes or short-circuit a save attempt via exceptions.

**Fires:** On every settings save (from the React admin or REST endpoint).

```php
do_action( 'eventkoi_before_save_settings', $settings );
```

- Pro: `includes/core/class-settings.php:87`
- Lite: `includes/core/class-settings.php:45`

#### `eventkoi_installed`

_Pro + Lite · action_

Fires the first time the plugin's bootstrap detects no installed version stored in `eventkoi_version` — i.e. on first activation.

**Fires:** From `Install::maybe_run()` after the initial schema is created.

```php
do_action( 'eventkoi_installed' );
```

- Pro: `includes/core/class-install.php:77`
- Lite: `includes/core/class-install.php:77`

#### `eventkoi_register_post_type`

_Pro + Lite · action_

Fires immediately before EventKoi registers its `eventkoi_event` post type. Use to register related post types alongside it (e.g. an addon's CPT) so they share the same registration cycle.

**Fires:** Once per request, inside `Post_Types::register_post_types()`.

```php
do_action( 'eventkoi_register_post_type' );
```

- Pro: `includes/core/class-post-types.php:95`
- Lite: `includes/core/class-post-types.php:95`

#### `eventkoi_register_rewrites`

_Pro + Lite · action_

Fires once when EventKoi is about to flush WordPress rewrite rules (e.g. after install or permalink-structure change). Hook this to register additional rewrite rules so they're included in the flush.

**Fires:** From `Install::maybe_flush_rewrite_rules()` immediately before `flush_rewrite_rules()`.

```php
do_action( 'eventkoi_register_rewrites' );
```

- Pro: `includes/core/class-install.php:194`
- Lite: `includes/core/class-install.php:177`

#### `eventkoi_register_taxonomy`

_Pro + Lite · action_

Fires immediately before EventKoi registers its `event_cal` taxonomy. Use to register related taxonomies on the same cycle.

**Fires:** Once per request, inside `Post_Types::register_taxonomies()`.

```php
do_action( 'eventkoi_register_taxonomy' );
```

- Pro: `includes/core/class-post-types.php:42`
- Lite: `includes/core/class-post-types.php:42`

#### `eventkoi_updated`

_Pro + Lite · action_

Fires when the bootstrap detects a version drift between the option `eventkoi_version` and the constant `EVENTKOI_VERSION`. Receives the previously-stored version and the now-current version.

**Fires:** From `Install::maybe_run()` after the schema upgrade routine completes.

```php
do_action( 'eventkoi_updated', $stored, $current );
```

- Pro: `includes/core/class-install.php:56`
- Lite: `includes/core/class-install.php:56`

---

_Total: **205 unique hooks** — 178 in both plugins, 27 Pro-only, 0 Lite-only._
