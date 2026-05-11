# EventKoi hooks & filters reference

Auto-generated inventory of every action and filter exposed by EventKoi Pro and Lite. Use these to extend the plugin without modifying core files.

- **Plugin column**: where the hook fires.
  - *Pro + Lite* — same hook in both plugins
  - *Pro only* — Pro-only feature
  - *Lite only* — Lite-only (rare)
- **File** is the location of the **first occurrence** of each hook in the plugin source.
- Hooks may fire from multiple call sites; the listed file is the canonical declaration.

## Contents
- [Events](#events) — 78 hooks (72 filters, 6 actions)
- [Calendars](#calendars) — 34 hooks (29 filters, 5 actions)
- [RSVPs](#rsvps) — 19 hooks (19 filters, 0 actions)
- [Tickets & checkout](#tickets-checkout) — 9 hooks (9 filters, 0 actions)
- [Blocks & shortcodes](#blocks-shortcodes) — 1 hooks (1 filters, 0 actions)
- [Query loop & integrations](#query-loop-integrations) — 1 hooks (1 filters, 0 actions)
- [Page builders](#page-builders) — 1 hooks (1 filters, 0 actions)
- [Admin & UI](#admin-ui) — 3 hooks (2 filters, 1 actions)
- [Other](#other) — 59 hooks (45 filters, 14 actions)

## Events

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_beaver_event_options_limit` | Pro + Lite | _See source for context._ |
| `eventkoi_divi_event_options_limit` | Pro + Lite | _See source for context._ |
| `eventkoi_event_series_template_args` | Pro + Lite | _See source for context._ |
| `eventkoi_event_template_args` | Pro + Lite | _See source for context._ |
| `eventkoi_get_default_event_template` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_attendance_mode` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_core_status` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_counts` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_days` | Pro + Lite | Filter the retrieved event days. |
| `eventkoi_get_event_description` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_dynamic_tags` | Pro only | _See source for context._ |
| `eventkoi_get_event_embed_gmap` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_end_date_iso` | Pro + Lite | Filters the ISO-formatted end date for an event. |
| `eventkoi_get_event_end_date_raw` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_gmap_link` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_ical` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_id` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_image` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_image_id` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_image_thumb` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_latitude` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_location` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_locations` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_longitude` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_post_status` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_recurrence_overrides` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_recurrence_rules` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_schema` | Pro + Lite | Allow developers to modify the schema. |
| `eventkoi_get_event_series_template` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_standard_type` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_start_date_iso` | Pro + Lite | Filters the ISO-formatted start date for an event. |
| `eventkoi_get_event_start_date_raw` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_status` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_tbc` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_tbc_note` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_thumbnail` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_tickets_display_mode` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_tickets_enabled` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_tickets_terms_conditions` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_timezone` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_title` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_type` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_url` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_virtual_url` | Pro + Lite | _See source for context._ |
| `eventkoi_pre_update_event_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_capacity` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_capacity_remaining` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_capacity_sold` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_day` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_day_name` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_iso` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_month` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_month_short` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_date_year` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_datetime` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_datetime_with_summary` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_details` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_image_url` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_location` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_low_stock` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_sales_end` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_sales_start` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_sold_out` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_tickets` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_time` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_timezone` | Pro + Lite | Filter the rendered timezone string for the event. |
| `eventkoi_rendered_event_title` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_type` | Pro only | _See source for context._ |
| `eventkoi_taxonomy_objects_event_cal` | Pro + Lite | _See source for context._ |
| `eventkoi_update_event_meta` | Pro + Lite | Hook to allow chnages to calendar metadata. |

#### Filter signatures

<details><summary><code>eventkoi_beaver_event_options_limit</code></summary>

**Signature:** `apply_filters( 'eventkoi_beaver_event_options_limit', 200 )`

- Pro: `includes/core/class-beaver-modules.php:422`
- Lite: `includes/core/class-beaver-modules.php:294`
</details>

<details><summary><code>eventkoi_divi_event_options_limit</code></summary>

**Signature:** `apply_filters( 'eventkoi_divi_event_options_limit', 200 )`

- Pro: `includes/core/divi-modules/class-et-builder-module-eventkoievent.php:146`
- Lite: `includes/core/divi-modules/class-et-builder-module-eventkoievent.php:146`
</details>

<details><summary><code>eventkoi_event_series_template_args</code></summary>

**Signature:** `apply_filters( 'eventkoi_event_series_template_args', $series_args ) )`

- Pro: `includes/core/class-template.php:172`
- Lite: `includes/core/class-template.php:166`
</details>

<details><summary><code>eventkoi_event_template_args</code></summary>

**Signature:** `apply_filters( 'eventkoi_event_template_args', $args ) )`

- Pro: `includes/core/class-template.php:161`
- Lite: `includes/core/class-template.php:155`
</details>

<details><summary><code>eventkoi_get_default_event_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_default_event_template', $content )`

- Pro: `includes/core/class-template.php:226`
- Lite: `includes/core/class-template.php:220`
</details>

<details><summary><code>eventkoi_get_event_attendance_mode</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_attendance_mode', $mode, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2475`
- Lite: `includes/core/class-event.php:1508`
</details>

<details><summary><code>eventkoi_get_event_core_status</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_core_status', $status, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1352`
- Lite: `includes/core/class-event.php:896`
</details>

<details><summary><code>eventkoi_get_event_counts</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_counts', $counts )`

- Pro: `includes/core/class-events.php:2037`
- Lite: `includes/core/class-events.php:436`
</details>

<details><summary><code>eventkoi_get_event_days</code></summary>

Filter the retrieved event days.

**Signature:** `apply_filters( 'eventkoi_get_event_days', $event_days, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:999`
- Lite: `includes/core/class-event.php:633`
</details>

<details><summary><code>eventkoi_get_event_description</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_description', wp_kses_post( $description ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1159`
- Lite: `includes/core/class-event.php:711`
</details>

<details><summary><code>eventkoi_get_event_dynamic_tags</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_dynamic_tags', $tags )`

- Pro: `includes/core/class-elementor-dynamic-tags.php:306`
</details>

<details><summary><code>eventkoi_get_event_embed_gmap</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_embed_gmap', (bool) $embed_gmap, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2273`
- Lite: `includes/core/class-event.php:1476`
</details>

<details><summary><code>eventkoi_get_event_end_date_iso</code></summary>

Filters the ISO-formatted end date for an event.

**Signature:** `apply_filters( 'eventkoi_get_event_end_date_iso', $iso, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1605`
- Lite: `includes/core/class-event.php:1137`
</details>

<details><summary><code>eventkoi_get_event_end_date_raw</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_end_date_raw', (string) $formatted, self::$event_id, self::$event, $gmt )`

- Pro: `includes/core/class-event.php:1505`
- Lite: `includes/core/class-event.php:1043`
</details>

<details><summary><code>eventkoi_get_event_gmap_link</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_gmap_link', (string) $gmap_link, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2282`
- Lite: `includes/core/class-event.php:1485`
</details>

<details><summary><code>eventkoi_get_event_ical</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_ical', $ical, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1301`
- Lite: `includes/core/class-event.php:848`
</details>

<details><summary><code>eventkoi_get_event_id</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_id', $id, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:966`
- Lite: `includes/core/class-event.php:600`
</details>

<details><summary><code>eventkoi_get_event_image</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_image', esc_url( $attachment_url ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1173`
- Lite: `includes/core/class-event.php:727`
</details>

<details><summary><code>eventkoi_get_event_image_id</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_image_id', absint( $image_id ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1215`
- Lite: `includes/core/class-event.php:764`
</details>

<details><summary><code>eventkoi_get_event_image_thumb</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_image_thumb', esc_url( $thumb ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1206`
- Lite: `includes/core/class-event.php:755`
</details>

<details><summary><code>eventkoi_get_event_latitude</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_latitude', (string) $latitude, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2255`
- Lite: `includes/core/class-event.php:1458`
</details>

<details><summary><code>eventkoi_get_event_location</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_location', $location, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2246`
- Lite: `includes/core/class-event.php:1449`
</details>

<details><summary><code>eventkoi_get_event_locations</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_locations', $locations, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1230`
- Lite: `includes/core/class-event.php:779`
</details>

<details><summary><code>eventkoi_get_event_longitude</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_longitude', (string) $longitude, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2264`
- Lite: `includes/core/class-event.php:1467`
</details>

<details><summary><code>eventkoi_get_event_meta</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_meta', $meta, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:195`
- Lite: `includes/core/class-event.php:186`
</details>

<details><summary><code>eventkoi_get_event_post_status</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_post_status', $post_status, $event_id )`

- Pro: `includes/core/core-functions.php:161`
- Lite: `includes/core/core-functions.php:113`
</details>

<details><summary><code>eventkoi_get_event_recurrence_overrides</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_recurrence_overrides', $overrides, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1084`
- Lite: `includes/core/class-event.php:673`
</details>

<details><summary><code>eventkoi_get_event_recurrence_rules</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_recurrence_rules', $rules, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1059`
- Lite: `includes/core/class-event.php:648`
</details>

<details><summary><code>eventkoi_get_event_schema</code></summary>

Allow developers to modify the schema.

**Signature:** `apply_filters( 'eventkoi_get_event_schema', $schema )`

- Pro: `includes/core/class-schema.php:190`
- Lite: `includes/core/class-schema.php:190`
</details>

<details><summary><code>eventkoi_get_event_series_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_series_template', $content )`

- Pro: `includes/core/class-template.php:300`
- Lite: `includes/core/class-template.php:294`
</details>

<details><summary><code>eventkoi_get_event_standard_type</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_standard_type', (string) $standard_type, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2218`
- Lite: `includes/core/class-event.php:1435`
</details>

<details><summary><code>eventkoi_get_event_start_date_iso</code></summary>

Filters the ISO-formatted start date for an event.

**Signature:** `apply_filters( 'eventkoi_get_event_start_date_iso', $iso, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1572`
- Lite: `includes/core/class-event.php:1104`
</details>

<details><summary><code>eventkoi_get_event_start_date_raw</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_start_date_raw', (string) $formatted, self::$event_id, self::$event, $gmt )`

- Pro: `includes/core/class-event.php:1439`
- Lite: `includes/core/class-event.php:983`
</details>

<details><summary><code>eventkoi_get_event_status</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_status', $status, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1343`
- Lite: `includes/core/class-event.php:887`
</details>

<details><summary><code>eventkoi_get_event_tbc</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_tbc', (bool) $tbc, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2084`
- Lite: `includes/core/class-event.php:1229`
</details>

<details><summary><code>eventkoi_get_event_tbc_note</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_tbc_note', (string) $tbc_note, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2102`
- Lite: `includes/core/class-event.php:1247`
</details>

<details><summary><code>eventkoi_get_event_thumbnail</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_thumbnail', esc_url( $thumbnail ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1095`
- Lite: `includes/core/class-event.php:684`
</details>

<details><summary><code>eventkoi_get_event_tickets_display_mode</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_tickets_display_mode', $mode, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2559`
- Lite: `includes/core/class-event.php:1591`
</details>

<details><summary><code>eventkoi_get_event_tickets_enabled</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_tickets_enabled', (bool) $enabled, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2486`
- Lite: `includes/core/class-event.php:1519`
</details>

<details><summary><code>eventkoi_get_event_tickets_terms_conditions</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_tickets_terms_conditions', $terms, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2497`
- Lite: `includes/core/class-event.php:1530`
</details>

<details><summary><code>eventkoi_get_event_timezone</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_timezone', (string) $timezone, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:977`
- Lite: `includes/core/class-event.php:611`
</details>

<details><summary><code>eventkoi_get_event_title</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_title', $title, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1150`
- Lite: `includes/core/class-event.php:702`
</details>

<details><summary><code>eventkoi_get_event_type</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_type', (string) $type, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2186`
- Lite: `includes/core/class-event.php:1422`
</details>

<details><summary><code>eventkoi_get_event_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_url', $url, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1283`
- Lite: `includes/core/class-event.php:830`
</details>

<details><summary><code>eventkoi_get_event_virtual_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_virtual_url', (string) $virtual_url, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2291`
- Lite: `includes/core/class-event.php:1494`
</details>

<details><summary><code>eventkoi_pre_update_event_meta</code></summary>

**Signature:** `apply_filters( 'eventkoi_pre_update_event_meta', $meta, $meta['id'] )`

- Pro: `includes/core/class-event.php:672`
- Lite: `includes/core/class-event.php:389`
</details>

<details><summary><code>eventkoi_rendered_event_capacity</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_capacity', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3758`
- Lite: `includes/core/class-event.php:2851`
</details>

<details><summary><code>eventkoi_rendered_event_capacity_remaining</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_capacity_remaining', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3769`
- Lite: `includes/core/class-event.php:2862`
</details>

<details><summary><code>eventkoi_rendered_event_capacity_sold</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_capacity_sold', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3780`
- Lite: `includes/core/class-event.php:2873`
</details>

<details><summary><code>eventkoi_rendered_event_date</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3285`
- Lite: `includes/core/class-event.php:2407`
</details>

<details><summary><code>eventkoi_rendered_event_date_day</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_day', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4097`
- Lite: `includes/core/class-event.php:3177`
</details>

<details><summary><code>eventkoi_rendered_event_date_day_name</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_day_name', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4108`
- Lite: `includes/core/class-event.php:3188`
</details>

<details><summary><code>eventkoi_rendered_event_date_iso</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_iso', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4119`
- Lite: `includes/core/class-event.php:3199`
</details>

<details><summary><code>eventkoi_rendered_event_date_month</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_month', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4075`
- Lite: `includes/core/class-event.php:3155`
</details>

<details><summary><code>eventkoi_rendered_event_date_month_short</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_month_short', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4086`
- Lite: `includes/core/class-event.php:3166`
</details>

<details><summary><code>eventkoi_rendered_event_date_year</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_date_year', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4064`
- Lite: `includes/core/class-event.php:3144`
</details>

<details><summary><code>eventkoi_rendered_event_datetime</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_datetime', $message, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3162`
- Lite: `includes/core/class-event.php:2291`
</details>

<details><summary><code>eventkoi_rendered_event_datetime_with_summary</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_datetime_with_summary', wp_kses_post( $line ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3190`
- Lite: `includes/core/class-event.php:2314`
</details>

<details><summary><code>eventkoi_rendered_event_details</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_details', $details, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2857`
- Lite: `includes/core/class-event.php:1986`
</details>

<details><summary><code>eventkoi_rendered_event_image_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_image_url', $url, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2913`
- Lite: `includes/core/class-event.php:2042`
</details>

<details><summary><code>eventkoi_rendered_event_location</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_location', implode( "\n\n", $outputs ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3055`
- Lite: `includes/core/class-event.php:2184`
</details>

<details><summary><code>eventkoi_rendered_event_low_stock</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_low_stock', '', self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3806`
- Lite: `includes/core/class-event.php:2899`
</details>

<details><summary><code>eventkoi_rendered_event_sales_end</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_sales_end', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3904`
- Lite: `includes/core/class-event.php:2994`
</details>

<details><summary><code>eventkoi_rendered_event_sales_start</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_sales_start', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3879`
- Lite: `includes/core/class-event.php:2969`
</details>

<details><summary><code>eventkoi_rendered_event_sold_out</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_sold_out', $label, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3792`
- Lite: `includes/core/class-event.php:2885`
</details>

<details><summary><code>eventkoi_rendered_event_tickets</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_tickets', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3134`
- Lite: `includes/core/class-event.php:2263`
</details>

<details><summary><code>eventkoi_rendered_event_time</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_time', '', self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3336`
- Lite: `includes/core/class-event.php:2458`
</details>

<details><summary><code>eventkoi_rendered_event_timezone</code></summary>

Filter the rendered timezone string for the event.

**Signature:** `apply_filters( 'eventkoi_rendered_event_timezone', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3096`
- Lite: `includes/core/class-event.php:2225`
</details>

<details><summary><code>eventkoi_rendered_event_title</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_title', $title, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2838`
- Lite: `includes/core/class-event.php:1968`
</details>

<details><summary><code>eventkoi_rendered_event_type</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_type', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2205`
</details>

<details><summary><code>eventkoi_taxonomy_objects_event_cal</code></summary>

**Signature:** `apply_filters( 'eventkoi_taxonomy_objects_event_cal', array( 'eventkoi_event' ) ),
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
			) )`

- Pro: `includes/core/class-post-types.php:48`
- Lite: `includes/core/class-post-types.php:48`
</details>

<details><summary><code>eventkoi_update_event_meta</code></summary>

Hook to allow chnages to calendar metadata.

**Signature:** `apply_filters( 'eventkoi_update_event_meta', $meta, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:466`
- Lite: `includes/core/class-calendar.php:334`
</details>


### Actions

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_after_event_content` | Pro + Lite | _See source for context._ |
| `eventkoi_after_update_event_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_before_event_content` | Pro + Lite | _See source for context._ |
| `eventkoi_before_update_event_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_event_posts_migrated` | Pro + Lite | Fires after EventKoi post type migration completes. |
| `eventkoi_single_event_template` | Pro + Lite | _See source for context._ |

#### Action signatures

<details><summary><code>eventkoi_after_event_content</code></summary>

**Signature:** `do_action( 'eventkoi_after_event_content' )`

- Pro: `templates/single-event-legacy.php:41`
- Lite: `templates/single-event-legacy.php:41`
</details>

<details><summary><code>eventkoi_after_update_event_meta</code></summary>

**Signature:** `do_action( 'eventkoi_after_update_event_meta', $meta, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:957`
- Lite: `includes/core/class-event.php:591`
</details>

<details><summary><code>eventkoi_before_event_content</code></summary>

**Signature:** `do_action( 'eventkoi_before_event_content' )`

- Pro: `templates/single-event-legacy.php:32`
- Lite: `templates/single-event-legacy.php:32`
</details>

<details><summary><code>eventkoi_before_update_event_meta</code></summary>

**Signature:** `do_action( 'eventkoi_before_update_event_meta', $meta, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:733`
- Lite: `includes/core/class-event.php:450`
</details>

<details><summary><code>eventkoi_event_posts_migrated</code></summary>

Fires after EventKoi post type migration completes.

**Signature:** `do_action( 'eventkoi_event_posts_migrated', count( $post_ids ) )`

- Pro: `includes/core/class-install.php:274`
- Lite: `includes/core/class-install.php:257`
</details>

<details><summary><code>eventkoi_single_event_template</code></summary>

**Signature:** `do_action( 'eventkoi_single_event_template', $post )`

- Pro: `templates/single-event-legacy.php:37`
- Lite: `templates/single-event-legacy.php:37`
</details>


## Calendars

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_calendar_display_max_results` | Pro only | _See source for context._ |
| `eventkoi_default_calendar_color` | Pro + Lite | Filter the default calendar color. |
| `eventkoi_get_calendar_color` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_content` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_count` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_day_start_time` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_default_month` | Pro + Lite | Filters the default month for the calendar. |
| `eventkoi_get_calendar_default_year` | Pro + Lite | Filters the default year for the calendar. |
| `eventkoi_get_calendar_display` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_id` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_list_date_end` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_date_start` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_expand_instances` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_load_mode` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_max_results` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_order` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_orderby` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_list_per_page` | Pro only | _See source for context._ |
| `eventkoi_get_calendar_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_name` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_shortcode` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_slug` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_startday` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_timeframe` | Pro + Lite | _See source for context._ |
| `eventkoi_get_calendar_url` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_calendar` | Pro + Lite | _See source for context._ |
| `eventkoi_pre_update_calendar_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_calendar` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_calendar_url` | Pro + Lite | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_calendar_display_max_results</code></summary>

**Signature:** `apply_filters( 'eventkoi_calendar_display_max_results', $max_results, array(
					'view_type'    => $view_type,
					'window_days'  => $window_days,
					'calendar_id'  => absint( $id ),
					'calendar_ids' => $ids,
				) )`

- Pro: `includes/api/class-calendar.php:288`
</details>

<details><summary><code>eventkoi_default_calendar_color</code></summary>

Filter the default calendar color.

**Signature:** `apply_filters( 'eventkoi_default_calendar_color', '#578CA7' )`

- Pro: `includes/core/core-functions.php:845`
- Lite: `includes/core/core-functions.php:775`
</details>

<details><summary><code>eventkoi_get_calendar_color</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_color', $color, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:384`
- Lite: `includes/core/class-calendar.php:252`
</details>

<details><summary><code>eventkoi_get_calendar_content</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_content', $calendar_template ) )`

- Pro: `includes/core/core-functions.php:546`
- Lite: `includes/core/core-functions.php:476`
</details>

<details><summary><code>eventkoi_get_calendar_count</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_count', $count, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:139`
- Lite: `includes/core/class-calendar.php:131`
</details>

<details><summary><code>eventkoi_get_calendar_day_start_time</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_day_start_time', $start_time, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:247`
- Lite: `includes/core/class-calendar.php:239`
</details>

<details><summary><code>eventkoi_get_calendar_default_month</code></summary>

Filters the default month for the calendar.

**Signature:** `apply_filters( 'eventkoi_get_calendar_default_month', $month, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:162`
- Lite: `includes/core/class-calendar.php:154`
</details>

<details><summary><code>eventkoi_get_calendar_default_year</code></summary>

Filters the default year for the calendar.

**Signature:** `apply_filters( 'eventkoi_get_calendar_default_year', $year, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:185`
- Lite: `includes/core/class-calendar.php:177`
</details>

<details><summary><code>eventkoi_get_calendar_display</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_display', $display, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:198`
- Lite: `includes/core/class-calendar.php:190`
</details>

<details><summary><code>eventkoi_get_calendar_id</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_id', $id, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:99`
- Lite: `includes/core/class-calendar.php:91`
</details>

<details><summary><code>eventkoi_get_calendar_list_date_end</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_date_end', $date_end, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:371`
</details>

<details><summary><code>eventkoi_get_calendar_list_date_start</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_date_start', $date_start, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:355`
</details>

<details><summary><code>eventkoi_get_calendar_list_expand_instances</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_expand_instances', $expand, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:339`
</details>

<details><summary><code>eventkoi_get_calendar_list_load_mode</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_load_mode', $mode, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:328`
</details>

<details><summary><code>eventkoi_get_calendar_list_max_results</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_max_results', $max_results, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:312`
</details>

<details><summary><code>eventkoi_get_calendar_list_order</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_order', $order, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:287`
</details>

<details><summary><code>eventkoi_get_calendar_list_orderby</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_orderby', $orderby, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:273`
</details>

<details><summary><code>eventkoi_get_calendar_list_per_page</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_list_per_page', $per_page, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:301`
</details>

<details><summary><code>eventkoi_get_calendar_meta</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_meta', $meta, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:90`
- Lite: `includes/core/class-calendar.php:82`
</details>

<details><summary><code>eventkoi_get_calendar_name</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_name', $name, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:108`
- Lite: `includes/core/class-calendar.php:100`
</details>

<details><summary><code>eventkoi_get_calendar_shortcode</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_shortcode', $shortcode, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:393`
- Lite: `includes/core/class-calendar.php:261`
</details>

<details><summary><code>eventkoi_get_calendar_slug</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_slug', $slug, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:117`
- Lite: `includes/core/class-calendar.php:109`
</details>

<details><summary><code>eventkoi_get_calendar_startday</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_startday', $startday, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:231`
- Lite: `includes/core/class-calendar.php:223`
</details>

<details><summary><code>eventkoi_get_calendar_timeframe</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_timeframe', $timeframe, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:211`
- Lite: `includes/core/class-calendar.php:203`
</details>

<details><summary><code>eventkoi_get_calendar_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_calendar_url', $url, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:130`
- Lite: `includes/core/class-calendar.php:122`
</details>

<details><summary><code>eventkoi_get_event_calendar</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_calendar', $calendar, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1252`
- Lite: `includes/core/class-event.php:801`
</details>

<details><summary><code>eventkoi_pre_update_calendar_meta</code></summary>

**Signature:** `apply_filters( 'eventkoi_pre_update_calendar_meta', $meta, $meta['id'] )`

- Pro: `includes/core/class-calendar.php:403`
- Lite: `includes/core/class-calendar.php:271`
</details>

<details><summary><code>eventkoi_rendered_event_calendar</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_calendar', implode( ', ', $names ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2963`
- Lite: `includes/core/class-event.php:2092`
</details>

<details><summary><code>eventkoi_rendered_event_calendar_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_calendar_url', $url, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2982`
- Lite: `includes/core/class-event.php:2111`
</details>


### Actions

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_after_calendar_content` | Pro + Lite | _See source for context._ |
| `eventkoi_after_update_calendar_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_before_calendar_content` | Pro + Lite | _See source for context._ |
| `eventkoi_before_update_calendar_meta` | Pro + Lite | _See source for context._ |
| `eventkoi_single_calendar_template` | Pro + Lite | _See source for context._ |

#### Action signatures

<details><summary><code>eventkoi_after_calendar_content</code></summary>

**Signature:** `do_action( 'eventkoi_after_calendar_content' )`

- Pro: `templates/single-calendar.php:39`
- Lite: `templates/single-calendar.php:39`
</details>

<details><summary><code>eventkoi_after_update_calendar_meta</code></summary>

**Signature:** `do_action( 'eventkoi_after_update_calendar_meta', $meta, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:532`
- Lite: `includes/core/class-calendar.php:356`
</details>

<details><summary><code>eventkoi_before_calendar_content</code></summary>

**Signature:** `do_action( 'eventkoi_before_calendar_content' )`

- Pro: `templates/single-calendar.php:34`
- Lite: `templates/single-calendar.php:34`
</details>

<details><summary><code>eventkoi_before_update_calendar_meta</code></summary>

**Signature:** `do_action( 'eventkoi_before_update_calendar_meta', $meta, self::$calendar_id, self::$calendar )`

- Pro: `includes/core/class-calendar.php:468`
- Lite: `includes/core/class-calendar.php:336`
</details>

<details><summary><code>eventkoi_single_calendar_template</code></summary>

**Signature:** `do_action( 'eventkoi_single_calendar_template' )`

- Pro: `templates/single-calendar.php:37`
- Lite: `templates/single-calendar.php:37`
</details>


## RSVPs

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_get_event_rsvp_allow_edit` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_allow_guests` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_auto_account` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_capacity` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_enabled` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_max_guests` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_sale_end` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_sale_start` | Pro + Lite | _See source for context._ |
| `eventkoi_get_event_rsvp_show_remaining` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_rsvp` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_rsvp_capacity` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_rsvp_full` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_rsvp_going` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_rsvp_remaining` | Pro + Lite | _See source for context._ |
| `eventkoi_rsvp_email_subject` | Pro + Lite | _See source for context._ |
| `eventkoi_rsvp_email_tags` | Pro + Lite | _See source for context._ |
| `eventkoi_rsvp_email_template` | Pro + Lite | _See source for context._ |
| `eventkoi_rsvp_qr_code` | Pro only | _See source for context._ |
| `eventkoi_rsvp_qr_url` | Pro only | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_get_event_rsvp_allow_edit</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_allow_edit', (bool) $allow_edit, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2380`
- Lite: `includes/core/class-event.php:1668`
</details>

<details><summary><code>eventkoi_get_event_rsvp_allow_guests</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_allow_guests', (bool) $allow_guests, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2353`
- Lite: `includes/core/class-event.php:1641`
</details>

<details><summary><code>eventkoi_get_event_rsvp_auto_account</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_auto_account', (bool) $auto_account, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2391`
- Lite: `includes/core/class-event.php:1679`
</details>

<details><summary><code>eventkoi_get_event_rsvp_capacity</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_capacity', $capacity, self::$event_id, self::$event, $instance_ts )`

- Pro: `includes/core/class-event.php:2326`
- Lite: `includes/core/class-event.php:1616`
</details>

<details><summary><code>eventkoi_get_event_rsvp_enabled</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_enabled', (bool) $enabled, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2302`
- Lite: `includes/core/class-event.php:1602`
</details>

<details><summary><code>eventkoi_get_event_rsvp_max_guests</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_max_guests', absint( $max_guests ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2364`
- Lite: `includes/core/class-event.php:1652`
</details>

<details><summary><code>eventkoi_get_event_rsvp_sale_end</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_sale_end', $end, self::$event_id, self::$event, $instance_ts )`

- Pro: `includes/core/class-event.php:2436`
- Lite: `includes/core/class-event.php:1706`
</details>

<details><summary><code>eventkoi_get_event_rsvp_sale_start</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_sale_start', $start, self::$event_id, self::$event, $instance_ts )`

- Pro: `includes/core/class-event.php:2414`
- Lite: `includes/core/class-event.php:1694`
</details>

<details><summary><code>eventkoi_get_event_rsvp_show_remaining</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_event_rsvp_show_remaining', (bool) $show_remaining, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2342`
- Lite: `includes/core/class-event.php:1630`
</details>

<details><summary><code>eventkoi_rendered_event_rsvp</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_rsvp', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3139`
- Lite: `includes/core/class-event.php:2268`
</details>

<details><summary><code>eventkoi_rendered_event_rsvp_capacity</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_rsvp_capacity', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4216`
- Lite: `includes/core/class-event.php:3261`
</details>

<details><summary><code>eventkoi_rendered_event_rsvp_full</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_rsvp_full', $label, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4249`
- Lite: `includes/core/class-event.php:3294`
</details>

<details><summary><code>eventkoi_rendered_event_rsvp_going</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_rsvp_going', (string) $snap['going'], self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4237`
- Lite: `includes/core/class-event.php:3282`
</details>

<details><summary><code>eventkoi_rendered_event_rsvp_remaining</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_rsvp_remaining', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4227`
- Lite: `includes/core/class-event.php:3272`
</details>

<details><summary><code>eventkoi_rsvp_email_subject</code></summary>

**Signature:** `apply_filters( 'eventkoi_rsvp_email_subject', $subject, $tags, $event_id, $instance_ts )`

- Pro: `includes/core/class-rsvps.php:1083`
- Lite: `includes/core/class-rsvps.php:970`
</details>

<details><summary><code>eventkoi_rsvp_email_tags</code></summary>

**Signature:** `apply_filters( 'eventkoi_rsvp_email_tags', $tags, $event_id, $instance_ts )`

- Pro: `includes/core/class-rsvps.php:1035`
- Lite: `includes/core/class-rsvps.php:925`
</details>

<details><summary><code>eventkoi_rsvp_email_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_rsvp_email_template', $default_body, $tags, $event_id, $instance_ts )`

- Pro: `includes/core/class-rsvps.php:1066`
- Lite: `includes/core/class-rsvps.php:953`
</details>

<details><summary><code>eventkoi_rsvp_qr_code</code></summary>

**Signature:** `apply_filters( 'eventkoi_rsvp_qr_code', $qr_code, $qr_url, $checkin_url, $token, $event_id, $instance_ts )`

- Pro: `includes/core/class-rsvps.php:958`
</details>

<details><summary><code>eventkoi_rsvp_qr_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_rsvp_qr_url', $qr_url, $checkin_url, $token, $event_id, $instance_ts )`

- Pro: `includes/core/class-rsvps.php:952`
</details>


## Tickets & checkout

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_rendered_event_ticket_count` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_ticket_price_from` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_ticket_price_range` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_ticket_price_to` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_event_ticket_summary` | Pro + Lite | _See source for context._ |
| `eventkoi_ticket_email_subject` | Pro + Lite | _See source for context._ |
| `eventkoi_ticket_email_tags` | Pro + Lite | _See source for context._ |
| `eventkoi_ticket_email_template` | Pro + Lite | _See source for context._ |
| `eventkoi_ticket_qr_url` | Pro only | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_rendered_event_ticket_count</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_ticket_count', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3833`
- Lite: `includes/core/class-event.php:2926`
</details>

<details><summary><code>eventkoi_rendered_event_ticket_price_from</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_ticket_price_from', $out, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3991`
- Lite: `includes/core/class-event.php:3071`
</details>

<details><summary><code>eventkoi_rendered_event_ticket_price_range</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_ticket_price_range', '', self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4020`
- Lite: `includes/core/class-event.php:3100`
</details>

<details><summary><code>eventkoi_rendered_event_ticket_price_to</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_ticket_price_to', '', self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:4002`
- Lite: `includes/core/class-event.php:3082`
</details>

<details><summary><code>eventkoi_rendered_event_ticket_summary</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_event_ticket_summary', $output, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:3851`
- Lite: `includes/core/class-event.php:2944`
</details>

<details><summary><code>eventkoi_ticket_email_subject</code></summary>

**Signature:** `apply_filters( 'eventkoi_ticket_email_subject', $subject_default, $tags, $order, $items )`

- Pro: `includes/core/class-ticket-emails.php:363`
- Lite: `includes/core/class-ticket-emails.php:337`
</details>

<details><summary><code>eventkoi_ticket_email_tags</code></summary>

**Signature:** `apply_filters( 'eventkoi_ticket_email_tags', $tags, $order, $items )`

- Pro: `includes/core/class-ticket-emails.php:360`
- Lite: `includes/core/class-ticket-emails.php:334`
</details>

<details><summary><code>eventkoi_ticket_email_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_ticket_email_template', $default_body, $tags, $order, $items )`

- Pro: `includes/core/class-ticket-emails.php:383`
- Lite: `includes/core/class-ticket-emails.php:356`
</details>

<details><summary><code>eventkoi_ticket_qr_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_ticket_qr_url', $qr_url, $checkin_url, $checkin_code, $event_id, $instance_ts )`

- Pro: `includes/core/class-ticket-emails.php:330`
</details>


## Blocks & shortcodes

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_block_live_stripe_on_staging` | Pro only | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_block_live_stripe_on_staging</code></summary>

**Signature:** `apply_filters( 'eventkoi_block_live_stripe_on_staging', true )
		) {
			return new \WP_Error(
				'eventkoi_stripe_live_on_staging',
				__( 'Live-mode Stripe keys cannot be connected on staging or local URLs. Use test-mode keys here.', 'eventkoi' ) )`

- Pro: `includes/payments/class-stripe.php:742`
</details>


## Query loop & integrations

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_loop_default_window_seconds` | Pro only | Window (in seconds) used when expanding recurring instances in a Beaver Builder loop without an explicit date range. |

#### Filter signatures

<details><summary><code>eventkoi_loop_default_window_seconds</code></summary>

Window (in seconds) used when expanding recurring instances in a Beaver Builder loop without an explicit date range.

**Signature:** `apply_filters( 'eventkoi_loop_default_window_seconds', YEAR_IN_SECONDS )`

- Pro: `includes/core/class-beaver-loop-query.php:182`
</details>


## Page builders

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_beaver_route_occurrence_query` | Pro only | Whether to route the current Beaver loop query through EventKoi occurrence matching. |

#### Filter signatures

<details><summary><code>eventkoi_beaver_route_occurrence_query</code></summary>

Whether to route the current Beaver loop query through EventKoi occurrence matching.

**Signature:** `apply_filters( 'eventkoi_beaver_route_occurrence_query', ( $has_temporal_filter || $orders_by_temporal || $instance_mode ), $args, $temporal, $orders_by_temporal )`

- Pro: `includes/core/class-beaver-loop-query.php:144`
</details>


## Admin & UI

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_admin_menu_items` | Pro + Lite | _See source for context._ |
| `eventkoi_admin_params` | Pro + Lite | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_admin_menu_items</code></summary>

**Signature:** `apply_filters( 'eventkoi_admin_menu_items', array(
				'dashboard' => __( 'Dashboard', 'eventkoi' ),
				'events'    => __( 'Events', 'eventkoi' ),
				'calendars' => __( 'Calendars', 'eventkoi' ),
				'tickets'   => __( 'Ticket sales', 'eventkoi' ),
				'settings'  => __( 'Settings', 'eventkoi' ),
			) )`

- Pro: `includes/admin/class-menus.php:119`
- Lite: `includes/admin/class-menus.php:148`
</details>

<details><summary><code>eventkoi_admin_params</code></summary>

**Signature:** `apply_filters( 'eventkoi_admin_params', $eventkoi_params ) )`

- Pro: `includes/admin/class-scripts.php:187`
- Lite: `includes/admin/class-scripts.php:252`
</details>


### Actions

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_admin_installed` | Pro + Lite | _See source for context._ |

#### Action signatures

<details><summary><code>eventkoi_admin_installed</code></summary>

**Signature:** `do_action( 'eventkoi_admin_installed' )`

- Pro: `includes/core/class-install.php:78`
- Lite: `includes/core/class-install.php:78`
</details>


## Other

### Filters

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_` | Pro + Lite | _See source for context._ |
| `eventkoi_currency` | Pro + Lite | _See source for context._ |
| `eventkoi_currency_locale` | Pro + Lite | _See source for context._ |
| `eventkoi_current_theme_support` | Pro + Lite | Filter the theme support detection result. |
| `eventkoi_field_date_format` | Pro + Lite | Filter the date format used for a specific field. |
| `eventkoi_frontend_params` | Pro + Lite | _See source for context._ |
| `eventkoi_get_content` | Pro + Lite | _See source for context._ |
| `eventkoi_get_custom_fields` | Pro only | _See source for context._ |
| `eventkoi_get_custom_fields_layout` | Pro only | _See source for context._ |
| `eventkoi_get_custom_fields_state` | Pro only | _See source for context._ |
| `eventkoi_get_default_date_format` | Pro + Lite | Filter the default date format used across EventKoi. |
| `eventkoi_get_default_template` | Pro + Lite | _See source for context._ |
| `eventkoi_get_end_date_g` | Pro + Lite | _See source for context._ |
| `eventkoi_get_footer` | Pro + Lite | Filter the block template content for the footer. |
| `eventkoi_get_header` | Pro + Lite | Filter the block template content for the header. |
| `eventkoi_get_order_stats` | Pro + Lite | _See source for context._ |
| `eventkoi_get_private_api_key` | Pro + Lite | _See source for context._ |
| `eventkoi_get_settings` | Pro + Lite | _See source for context._ |
| `eventkoi_get_start_date_g` | Pro + Lite | _See source for context._ |
| `eventkoi_get_status_title` | Pro + Lite | Filter the human-readable label for a status. |
| `eventkoi_get_stripe_currency` | Pro only | _See source for context._ |
| `eventkoi_get_stripe_webhook_secret` | Pro + Lite | Filters the Stripe webhook secret. |
| `eventkoi_get_summary` | Pro + Lite | Filter event excerpt. |
| `eventkoi_get_summary_from_string` | Pro only | Filters the generated summary string. |
| `eventkoi_get_template_asset` | Pro + Lite | Filter the template asset URL. |
| `eventkoi_get_timezone_display` | Pro + Lite | _See source for context._ |
| `eventkoi_live_mode_enabled` | Pro + Lite | Filter whether live mode is enabled. |
| `eventkoi_locate_template` | Pro + Lite | Allow developers to override via filter. |
| `eventkoi_login_url` | Pro only | _See source for context._ |
| `eventkoi_low_stock_threshold` | Pro + Lite | Override the "low stock" threshold. |
| `eventkoi_max_recurrence_iterations` | Pro + Lite | _See source for context._ |
| `eventkoi_max_upload_size_mb` | Pro + Lite | _See source for context._ |
| `eventkoi_pre_setting_value` | Pro + Lite | _See source for context._ |
| `eventkoi_prepare_raw_db_data` | Pro + Lite | Wrap it in an array and apply the filter. |
| `eventkoi_qr_checkin_capability` | Pro only | Capability required to perform a QR check-in. |
| `eventkoi_raw_client_ip` | Pro + Lite | Filter the sanitized client IP address. |
| `eventkoi_refund_email_subject` | Pro + Lite | _See source for context._ |
| `eventkoi_refund_email_tags` | Pro + Lite | _See source for context._ |
| `eventkoi_refund_email_template` | Pro + Lite | _See source for context._ |
| `eventkoi_rendered_custom_field` | Pro only | _See source for context._ |
| `eventkoi_rendered_custom_field_group` | Pro only | _See source for context._ |
| `eventkoi_rendered_custom_fields` | Pro only | _See source for context._ |
| `eventkoi_rendered_meta_for_` | Pro + Lite | _See source for context._ |
| `eventkoi_set_settings` | Pro + Lite | _See source for context._ |
| `eventkoi_timezone` | Pro + Lite | _See source for context._ |

#### Filter signatures

<details><summary><code>eventkoi_</code></summary>

**Signature:** `apply_filters( 'eventkoi_', . $name . '_output', self::$method(), self::get_id() )`

- Pro: `includes/core/class-event.php:276`
- Lite: `includes/core/class-event.php:258`
</details>

<details><summary><code>eventkoi_currency</code></summary>

**Signature:** `apply_filters( 'eventkoi_currency', strtolower( $currency ) )`

- Pro: `includes/core/class-stats.php:47`
- Lite: `includes/core/class-stats.php:42`
</details>

<details><summary><code>eventkoi_currency_locale</code></summary>

**Signature:** `apply_filters( 'eventkoi_currency_locale', $locale, $results[ $key ] )`

- Pro: `includes/core/class-hooks.php:306`
- Lite: `includes/core/class-hooks.php:239`
</details>

<details><summary><code>eventkoi_current_theme_support</code></summary>

Filter the theme support detection result.

**Signature:** `apply_filters( 'eventkoi_current_theme_support', $support )`

- Pro: `includes/core/core-functions.php:633`
- Lite: `includes/core/core-functions.php:563`
</details>

<details><summary><code>eventkoi_field_date_format</code></summary>

Filter the date format used for a specific field.

**Signature:** `apply_filters( 'eventkoi_field_date_format', $format, $field )`

- Pro: `includes/core/core-functions.php:1020`
- Lite: `includes/core/core-functions.php:908`
</details>

<details><summary><code>eventkoi_frontend_params</code></summary>

**Signature:** `apply_filters( 'eventkoi_frontend_params', $params ) )`

- Pro: `includes/core/class-scripts.php:152`
- Lite: `includes/core/class-scripts.php:145`
</details>

<details><summary><code>eventkoi_get_content</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_content', $default_template->post_content ) )`

- Pro: `includes/core/core-functions.php:339`
- Lite: `includes/core/core-functions.php:306`
</details>

<details><summary><code>eventkoi_get_custom_fields</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_custom_fields', $fields, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1959`
</details>

<details><summary><code>eventkoi_get_custom_fields_layout</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_custom_fields_layout', null, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1114`
</details>

<details><summary><code>eventkoi_get_custom_fields_state</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_custom_fields_state', null, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1133`
</details>

<details><summary><code>eventkoi_get_default_date_format</code></summary>

Filter the default date format used across EventKoi.

**Signature:** `apply_filters( 'eventkoi_get_default_date_format', $date_format )`

- Pro: `includes/core/core-functions.php:659`
- Lite: `includes/core/core-functions.php:589`
</details>

<details><summary><code>eventkoi_get_default_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_default_template', $content )`

- Pro: `includes/core/class-blocks.php:2303`
- Lite: `includes/core/class-blocks.php:1888`
</details>

<details><summary><code>eventkoi_get_end_date_g</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_end_date_g', eventkoi_format_gcal_datetime( $raw ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1536`
- Lite: `includes/core/class-event.php:1068`
</details>

<details><summary><code>eventkoi_get_footer</code></summary>

Filter the block template content for the footer.

**Signature:** `apply_filters( 'eventkoi_get_footer', $content ) )`

- Pro: `includes/core/core-functions.php:323`
- Lite: `includes/core/core-functions.php:288`
</details>

<details><summary><code>eventkoi_get_header</code></summary>

Filter the block template content for the header.

**Signature:** `apply_filters( 'eventkoi_get_header', $content ) )`

- Pro: `includes/core/core-functions.php:300`
- Lite: `includes/core/core-functions.php:265`
</details>

<details><summary><code>eventkoi_get_order_stats</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_order_stats', $stats )`

- Pro: `includes/core/class-stats.php:63`
- Lite: `includes/core/class-stats.php:58`
</details>

<details><summary><code>eventkoi_get_private_api_key</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_private_api_key', esc_attr( $api_key ) )`

- Pro: `includes/api/class-rest.php:167`
- Lite: `includes/api/class-rest.php:159`
</details>

<details><summary><code>eventkoi_get_settings</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_settings', $settings )`

- Pro: `includes/core/class-settings.php:44`
- Lite: `includes/core/class-settings.php:35`
</details>

<details><summary><code>eventkoi_get_start_date_g</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_start_date_g', eventkoi_format_gcal_datetime( $raw ), self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:1521`
- Lite: `includes/core/class-event.php:1053`
</details>

<details><summary><code>eventkoi_get_status_title</code></summary>

Filter the human-readable label for a status.

**Signature:** `apply_filters( 'eventkoi_get_status_title', $label, $status )`

- Pro: `includes/core/core-functions.php:876`
- Lite: `includes/core/core-functions.php:806`
</details>

<details><summary><code>eventkoi_get_stripe_currency</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_stripe_currency', $currency )`

- Pro: `includes/payments/class-stripe.php:934`
</details>

<details><summary><code>eventkoi_get_stripe_webhook_secret</code></summary>

Filters the Stripe webhook secret.

**Signature:** `apply_filters( 'eventkoi_get_stripe_webhook_secret', $webhook_secret )`

- Pro: `includes/core/core-functions.php:918`
- Lite: `includes/core/core-functions.php:1233`
</details>

<details><summary><code>eventkoi_get_summary</code></summary>

Filter event excerpt.

**Signature:** `apply_filters( 'eventkoi_get_summary', $summary, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2778`
- Lite: `includes/core/class-event.php:1908`
</details>

<details><summary><code>eventkoi_get_summary_from_string</code></summary>

Filters the generated summary string.

**Signature:** `apply_filters( 'eventkoi_get_summary_from_string', $content, $max_chars )`

- Pro: `includes/core/core-functions.php:134`
</details>

<details><summary><code>eventkoi_get_template_asset</code></summary>

Filter the template asset URL.

**Signature:** `apply_filters( 'eventkoi_get_template_asset', $url, $asset )`

- Pro: `includes/core/core-functions.php:277`
- Lite: `includes/core/core-functions.php:242`
</details>

<details><summary><code>eventkoi_get_timezone_display</code></summary>

**Signature:** `apply_filters( 'eventkoi_get_timezone_display', (bool) $timezone_display, self::$event_id, self::$event )`

- Pro: `includes/core/class-event.php:2093`
- Lite: `includes/core/class-event.php:1238`
</details>

<details><summary><code>eventkoi_live_mode_enabled</code></summary>

Filter whether live mode is enabled.

**Signature:** `apply_filters( 'eventkoi_live_mode_enabled', $live )`

- Pro: `includes/core/core-functions.php:935`
- Lite: `includes/core/core-functions.php:823`
</details>

<details><summary><code>eventkoi_locate_template</code></summary>

Allow developers to override via filter.

**Signature:** `apply_filters( 'eventkoi_locate_template', $template, $template_name, $default_path )`

- Pro: `includes/core/core-functions.php:1174`
- Lite: `includes/core/core-functions.php:1062`
</details>

<details><summary><code>eventkoi_login_url</code></summary>

**Signature:** `apply_filters( 'eventkoi_login_url', wp_login_url() ), )`

- Pro: `includes/core/class-scripts.php:143`
</details>

<details><summary><code>eventkoi_low_stock_threshold</code></summary>

Override the "low stock" threshold.

**Signature:** `apply_filters( 'eventkoi_low_stock_threshold', $default_threshold, self::$event_id, $snap['capacity'] )`

- Pro: `includes/core/class-event.php:3817`
- Lite: `includes/core/class-event.php:2910`
</details>

<details><summary><code>eventkoi_max_recurrence_iterations</code></summary>

**Signature:** `apply_filters( 'eventkoi_max_recurrence_iterations', 500 )`

- Pro: `includes/core/class-beaver-loop-query.php:1781`
- Lite: `includes/core/class-event.php:3635`
</details>

<details><summary><code>eventkoi_max_upload_size_mb</code></summary>

**Signature:** `apply_filters( 'eventkoi_max_upload_size_mb', 5 )`

- Pro: `includes/api/class-uploads.php:115`
- Lite: `includes/api/class-uploads.php:122`
</details>

<details><summary><code>eventkoi_pre_setting_value</code></summary>

**Signature:** `apply_filters( 'eventkoi_pre_setting_value', $sanitized, $key )`

- Pro: `includes/api/class-settings.php:170`
- Lite: `includes/api/class-settings.php:174`
</details>

<details><summary><code>eventkoi_prepare_raw_db_data</code></summary>

Wrap it in an array and apply the filter.

**Signature:** `apply_filters( 'eventkoi_prepare_raw_db_data', array( (object) $data ), 'order' )`

- Pro: `includes/api/class-order.php:71`
- Lite: `includes/api/class-order.php:73`
</details>

<details><summary><code>eventkoi_qr_checkin_capability</code></summary>

Capability required to perform a QR check-in.

**Signature:** `apply_filters( 'eventkoi_qr_checkin_capability', 'manage_options' )`

- Pro: `includes/core/class-qr-checkin.php:77`
</details>

<details><summary><code>eventkoi_raw_client_ip</code></summary>

Filter the sanitized client IP address.

**Signature:** `apply_filters( 'eventkoi_raw_client_ip', $raw_ip )`

- Pro: `includes/core/core-functions.php:993`
- Lite: `includes/core/core-functions.php:881`
</details>

<details><summary><code>eventkoi_refund_email_subject</code></summary>

**Signature:** `apply_filters( 'eventkoi_refund_email_subject', $subject_raw, $tags, $order )`

- Pro: `includes/core/class-ticket-emails.php:512`
- Lite: `includes/core/class-ticket-emails.php:479`
</details>

<details><summary><code>eventkoi_refund_email_tags</code></summary>

**Signature:** `apply_filters( 'eventkoi_refund_email_tags', $tags, $order, $refund_items )`

- Pro: `includes/core/class-ticket-emails.php:506`
- Lite: `includes/core/class-ticket-emails.php:473`
</details>

<details><summary><code>eventkoi_refund_email_template</code></summary>

**Signature:** `apply_filters( 'eventkoi_refund_email_template', $body, $tags, $order )`

- Pro: `includes/core/class-ticket-emails.php:534`
- Lite: `includes/core/class-ticket-emails.php:501`
</details>

<details><summary><code>eventkoi_rendered_custom_field</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_custom_field', $value, $field_key, self::$event_id, $show_label )`

- Pro: `includes/core/class-event.php:319`
</details>

<details><summary><code>eventkoi_rendered_custom_field_group</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_custom_field_group', $output, $group_key, self::$event_id, $show_labels )`

- Pro: `includes/core/class-event.php:393`
</details>

<details><summary><code>eventkoi_rendered_custom_fields</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_custom_fields', $output, self::$event_id )`

- Pro: `includes/core/class-event.php:514`
</details>

<details><summary><code>eventkoi_rendered_meta_for_</code></summary>

**Signature:** `apply_filters( 'eventkoi_rendered_meta_for_', . $key, $value, self::$event_id )`

- Pro: `includes/core/class-event.php:521`
- Lite: `includes/core/class-event.php:279`
</details>

<details><summary><code>eventkoi_set_settings</code></summary>

**Signature:** `apply_filters( 'eventkoi_set_settings', $settings ) )`

- Pro: `includes/core/class-settings.php:96`
- Lite: `includes/core/class-settings.php:49`
</details>

<details><summary><code>eventkoi_timezone</code></summary>

**Signature:** `apply_filters( 'eventkoi_timezone', $timezone )`

- Pro: `includes/core/core-functions.php:780`
- Lite: `includes/core/core-functions.php:710`
</details>


### Actions

| Hook | Plugin | Description |
|------|--------|-------------|
| `eventkoi_after_events_deleted` | Pro + Lite | Fires after soft-deleting multiple events. |
| `eventkoi_after_events_duplicated` | Pro + Lite | Fires after duplicating events. |
| `eventkoi_after_events_removed` | Pro + Lite | Fires after permanently removing events. |
| `eventkoi_after_events_restored` | Pro + Lite | Fires after restoring events from trash. |
| `eventkoi_after_order_created` | Pro + Lite | Fires after order has been created. |
| `eventkoi_after_order_updated` | Pro + Lite | _See source for context._ |
| `eventkoi_after_register_post_type` | Pro + Lite | _See source for context._ |
| `eventkoi_after_register_taxonomy` | Pro + Lite | _See source for context._ |
| `eventkoi_before_save_settings` | Pro + Lite | _See source for context._ |
| `eventkoi_installed` | Pro + Lite | _See source for context._ |
| `eventkoi_register_post_type` | Pro + Lite | _See source for context._ |
| `eventkoi_register_rewrites` | Pro + Lite | Let all custom rewrite rules register first. |
| `eventkoi_register_taxonomy` | Pro + Lite | _See source for context._ |
| `eventkoi_updated` | Pro + Lite | _See source for context._ |

#### Action signatures

<details><summary><code>eventkoi_after_events_deleted</code></summary>

Fires after soft-deleting multiple events.

**Signature:** `do_action( 'eventkoi_after_events_deleted', $ids )`

- Pro: `includes/api/class-events.php:208`
- Lite: `includes/api/class-events.php:194`
</details>

<details><summary><code>eventkoi_after_events_duplicated</code></summary>

Fires after duplicating events.

**Signature:** `do_action( 'eventkoi_after_events_duplicated', $ids )`

- Pro: `includes/api/class-events.php:282`
- Lite: `includes/api/class-events.php:268`
</details>

<details><summary><code>eventkoi_after_events_removed</code></summary>

Fires after permanently removing events.

**Signature:** `do_action( 'eventkoi_after_events_removed', $ids )`

- Pro: `includes/api/class-events.php:230`
- Lite: `includes/api/class-events.php:216`
</details>

<details><summary><code>eventkoi_after_events_restored</code></summary>

Fires after restoring events from trash.

**Signature:** `do_action( 'eventkoi_after_events_restored', $ids )`

- Pro: `includes/api/class-events.php:252`
- Lite: `includes/api/class-events.php:238`
</details>

<details><summary><code>eventkoi_after_order_created</code></summary>

Fires after order has been created.

**Signature:** `do_action( 'eventkoi_after_order_created', $args, $gateway )`

- Pro: `includes/core/class-orders.php:44`
- Lite: `includes/core/class-orders.php:39`
</details>

<details><summary><code>eventkoi_after_order_updated</code></summary>

**Signature:** `do_action( 'eventkoi_after_order_updated', $args, $gateway )`

- Pro: `includes/core/class-order.php:120`
- Lite: `includes/core/class-order.php:120`
</details>

<details><summary><code>eventkoi_after_register_post_type</code></summary>

**Signature:** `do_action( 'eventkoi_after_register_post_type' )`

- Pro: `includes/core/class-post-types.php:162`
- Lite: `includes/core/class-post-types.php:162`
</details>

<details><summary><code>eventkoi_after_register_taxonomy</code></summary>

**Signature:** `do_action( 'eventkoi_after_register_taxonomy' )`

- Pro: `includes/core/class-post-types.php:84`
- Lite: `includes/core/class-post-types.php:84`
</details>

<details><summary><code>eventkoi_before_save_settings</code></summary>

**Signature:** `do_action( 'eventkoi_before_save_settings', $settings )`

- Pro: `includes/core/class-settings.php:87`
- Lite: `includes/core/class-settings.php:45`
</details>

<details><summary><code>eventkoi_installed</code></summary>

**Signature:** `do_action( 'eventkoi_installed' )`

- Pro: `includes/core/class-install.php:77`
- Lite: `includes/core/class-install.php:77`
</details>

<details><summary><code>eventkoi_register_post_type</code></summary>

**Signature:** `do_action( 'eventkoi_register_post_type' )`

- Pro: `includes/core/class-post-types.php:95`
- Lite: `includes/core/class-post-types.php:95`
</details>

<details><summary><code>eventkoi_register_rewrites</code></summary>

Let all custom rewrite rules register first.

**Signature:** `do_action( 'eventkoi_register_rewrites' )`

- Pro: `includes/core/class-install.php:194`
- Lite: `includes/core/class-install.php:177`
</details>

<details><summary><code>eventkoi_register_taxonomy</code></summary>

**Signature:** `do_action( 'eventkoi_register_taxonomy' )`

- Pro: `includes/core/class-post-types.php:42`
- Lite: `includes/core/class-post-types.php:42`
</details>

<details><summary><code>eventkoi_updated</code></summary>

**Signature:** `do_action( 'eventkoi_updated', $stored, $current )`

- Pro: `includes/core/class-install.php:56`
- Lite: `includes/core/class-install.php:56`
</details>


---

_Total: 205 unique hooks — 178 in both plugins, 27 Pro-only, 0 Lite-only._
