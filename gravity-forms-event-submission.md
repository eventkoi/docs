# EventKoi — Frontend Event Submission with Gravity Forms

A complete, tested walkthrough for accepting **public event submissions** through Gravity Forms and turning each submission into a properly structured **draft `eventkoi_event`** that an admin can review and publish.

This guide pairs with the [Event Submission Field Reference](./event-submission-fields.md), which documents the underlying data model.

---

## What you'll build

- A public **Submit an Event** page powered by a Gravity Form
- A small handler that converts each submission into a draft `eventkoi_event` with the correct EventKoi data shape:
  - `event_days` array with UTC ISO datetimes
  - `locations` array (physical or virtual)
  - `event_cal` taxonomy term
  - `attendance_mode`, `timezone`, `description`, etc.
- An **approval workflow** — events land as `draft`, admins review and publish from wp-admin → EventKoi → Events.

---

## Prerequisites

- **EventKoi** Lite or Pro installed and active
- **Gravity Forms** installed and active (any current version)
- At least one calendar created in **EventKoi → Calendars** (to populate the calendar dropdown)
- Access to either an `mu-plugins/` directory **or** a code-snippets plugin to install the handler

---

## Step 1 — Create the form

In **Forms → New Form**, create a form titled **Submit an Event** with these fields **in this order**. Field IDs must match the snippet in Step 2.

| Field ID | Type | Label | Required | Notes |
|---|---|---|---|---|
| 1 | Single Line Text | Event title | ✓ | Becomes `post_title`. |
| 2 | Paragraph Text | Description | ✓ | Becomes `post_content` and the `description` meta. |
| 3 | Date | Start date | ✓ | Date format **YMD** (Date Field → Advanced → Date Format). |
| 4 | Time | Start time |   | 24-hour format. Leave blank if all-day. |
| 5 | Date | End date | ✓ | Date format **YMD**. |
| 6 | Time | End time |   | 24-hour format. Leave blank if all-day. |
| 7 | Single Checkbox | All-day event |   | One choice, value `yes`. When checked, times are ignored. |
| 8 | Single Line Text | Venue name |   | Physical location name. |
| 9 | Single Line Text | Venue address |   | Address line. |
| 10 | Drop Down | Calendar | optional | Choices = your EventKoi calendars. The **value** of each choice must be the calendar's term ID (e.g. `15508`). See [Calendar assignment modes](#calendar-assignment-modes) below. |

Gravity Forms assigns field IDs in creation order; the snippet hard-codes `1` through `10`. If you reorder or insert fields, update the IDs in the snippet to match.

### Calendar assignment modes

You don't have to ask the submitter which calendar their event belongs in. Pick the mode that matches your editorial workflow:

| Mode | Form behaviour | What the handler does |
|---|---|---|
| **Required** | Field 10 is required. Submitter must pick a calendar. | Uses their choice. |
| **Optional** (default in the snippet below) | Field 10 is optional. Submitter may leave it blank. | Falls back to the `eventkoi_default_submission_calendar` option if blank, otherwise leaves the event unassigned. |
| **Hidden** | Remove field 10 entirely. | Always uses the `eventkoi_default_submission_calendar` option. Admin reroutes at review time. |

Set the fallback calendar once:

```php
update_option( 'eventkoi_default_submission_calendar', <YOUR_CALENDAR_TERM_ID> );
```

The handler in Step 2 already wires the fallback — if the form submission doesn't carry a calendar term, the handler reads this option.

### Why field IDs matter

Gravity Forms stores submitted values keyed by field ID (e.g. `$entry['3']` for the start date). The handler reads those exact keys, so the IDs are part of the contract.

### Tip — populate the calendar dropdown automatically

Instead of typing each calendar's term ID by hand, paste this filter into your handler file (Step 2) so the dropdown stays in sync with `event_cal` terms:

```php
add_filter( 'gform_pre_render_1', 'ek_gf_inject_calendar_choices' );
add_filter( 'gform_pre_validation_1', 'ek_gf_inject_calendar_choices' );
add_filter( 'gform_admin_pre_render_1', 'ek_gf_inject_calendar_choices' );
add_filter( 'gform_form_pre_post_render', 'ek_gf_inject_calendar_choices' );
function ek_gf_inject_calendar_choices( $form ) {
    foreach ( $form['fields'] as &$field ) {
        if ( (int) $field->id !== 10 ) {
            continue;
        }
        $choices = array();
        foreach ( get_terms( array( 'taxonomy' => 'event_cal', 'hide_empty' => false ) ) as $term ) {
            $choices[] = array( 'text' => $term->name, 'value' => (string) $term->term_id );
        }
        $field->choices = $choices;
    }
    return $form;
}
```

Replace the `_1` suffix on the first three filters with your actual form ID.

---

## Step 2 — Install the submission handler

Drop the following file into `wp-content/mu-plugins/eventkoi-gf-handler.php`. It runs every time the form is submitted, builds an EventKoi-shaped draft event, and assigns the calendar term.

```php
<?php
/**
 * Plugin Name: EventKoi — Gravity Forms event submission handler
 * Description: Converts a Gravity Forms submission into a draft eventkoi_event.
 */

if ( ! defined( 'ABSPATH' ) ) {
    exit;
}

// Set this to the form ID from Step 1.
if ( ! defined( 'EKGF_FORM_ID' ) ) {
    define( 'EKGF_FORM_ID', 1 );
}

add_action( 'gform_after_submission', function ( $entry, $form ) {
    if ( (int) $form['id'] !== EKGF_FORM_ID ) {
        return;
    }

    $title       = trim( (string) rgar( $entry, '1' ) );
    $description = (string) rgar( $entry, '2' );
    $start_date  = (string) rgar( $entry, '3' );   // YYYY-MM-DD
    $start_time  = (string) rgar( $entry, '4' );   // HH:mm
    $end_date    = (string) rgar( $entry, '5' );   // YYYY-MM-DD
    $end_time    = (string) rgar( $entry, '6' );   // HH:mm
    $all_day_raw = (string) rgar( $entry, '7.1' ); // 'yes' when checked
    $venue_name  = trim( (string) rgar( $entry, '8' ) );
    $venue_addr  = trim( (string) rgar( $entry, '9' ) );
    $cal_term_id = (int) rgar( $entry, '10' );

    if ( '' === $title || '' === $start_date || '' === $end_date ) {
        return;
    }

    $is_all_day = ( 'yes' === strtolower( $all_day_raw ) );
    $site_tz    = wp_timezone();

    try {
        $start_wall = $is_all_day
            ? new DateTimeImmutable( $start_date . ' 00:00:00', $site_tz )
            : new DateTimeImmutable(
                $start_date . ' ' . ( '' !== $start_time ? $start_time : '00:00' ) . ':00',
                $site_tz
            );

        $end_wall = $is_all_day
            ? new DateTimeImmutable( $end_date . ' 23:59:59', $site_tz )
            : new DateTimeImmutable(
                $end_date . ' ' . ( '' !== $end_time ? $end_time : '23:59' ) . ':00',
                $site_tz
            );
    } catch ( Exception $e ) {
        return;
    }

    if ( $end_wall < $start_wall ) {
        $end_wall = $start_wall;
    }

    $utc = new DateTimeZone( 'UTC' );

    $event_id = wp_insert_post(
        array(
            'post_type'    => 'eventkoi_event',
            'post_status'  => 'draft',
            'post_title'   => wp_strip_all_tags( $title ),
            'post_content' => wp_kses_post( $description ),
        ),
        true
    );

    if ( is_wp_error( $event_id ) || ! $event_id ) {
        return;
    }

    update_post_meta( $event_id, 'description', $description );

    $start_utc      = $start_wall->setTimezone( $utc );
    $end_utc        = $end_wall->setTimezone( $utc );
    $start_iso      = $start_utc->format( 'Y-m-d\TH:i:s\Z' );
    $end_iso        = $end_utc->format( 'Y-m-d\TH:i:s\Z' );
    $start_mysql    = $start_utc->format( 'Y-m-d H:i:s' );
    $end_mysql      = $end_utc->format( 'Y-m-d H:i:s' );
    $start_ts       = $start_utc->getTimestamp();
    $end_ts         = $end_utc->getTimestamp();
    $is_multi_day   = ( $start_wall->format( 'Y-m-d' ) !== $end_wall->format( 'Y-m-d' ) );
    $standard_type  = $is_multi_day ? 'continuous' : 'single';

    update_post_meta( $event_id, 'date_type', 'standard' );
    update_post_meta( $event_id, 'standard_type', $standard_type );

    update_post_meta(
        $event_id,
        'event_days',
        array(
            array(
                'start_date' => $start_iso,
                'end_date'   => $end_iso,
                'all_day'    => $is_all_day,
            ),
        )
    );

    // Denormalized companion fields. EventKoi reads these for upcoming-index
    // queries, REST orderby=start_date, the Events admin table, and the
    // upcoming-events dashboard widget. Skipping them silently breaks all of
    // those surfaces — set them every time you write event_days.
    update_post_meta( $event_id, 'start_date', $start_mysql );
    update_post_meta( $event_id, 'end_date', $end_mysql );
    update_post_meta( $event_id, 'start_timestamp', $start_ts );
    update_post_meta( $event_id, 'end_timestamp', $end_ts );

    update_post_meta( $event_id, 'timezone', wp_timezone_string() );

    if ( '' !== $venue_name || '' !== $venue_addr ) {
        update_post_meta(
            $event_id,
            'locations',
            array(
                array(
                    'type'     => 'physical',
                    'name'     => $venue_name,
                    'address1' => $venue_addr,
                ),
            )
        );
    }

    update_post_meta( $event_id, 'attendance_mode', 'none' );

    // Calendar: use the submitter's choice if any, otherwise fall back to the
    // configured default-submission-calendar, otherwise leave the event
    // unassigned for the admin to set at review time.
    if ( $cal_term_id <= 0 ) {
        $cal_term_id = (int) get_option( 'eventkoi_default_submission_calendar', 0 );
    }
    if ( $cal_term_id > 0 ) {
        wp_set_post_terms( $event_id, array( $cal_term_id ), 'event_cal', false );
    }

    // ---- Custom fields ----
    // To expose an EventKoi custom field on the form, add ONE line below:
    //   <GF field ID> => '<eventkoi field_key>',
    // The EventKoi field must already exist under Settings → Custom fields.
    // The "field_key" is the slug shown there (without the `event_field_` prefix).
    $custom_field_map = array(
        // 11 => 'cost',
        // 12 => 'dress_code',
    );

    $custom_field_keys = array();
    foreach ( $custom_field_map as $gf_field_id => $ek_field_key ) {
        $raw = rgar( $entry, (string) $gf_field_id );
        if ( null === $raw ) {
            continue;
        }
        if ( is_array( $raw ) ) {
            $value = array_values(
                array_filter(
                    array_map( 'sanitize_text_field', $raw ),
                    static fn( $v ) => '' !== $v
                )
            );
            if ( empty( $value ) ) {
                continue;
            }
        } else {
            $value = trim( (string) $raw );
            if ( '' === $value ) {
                continue;
            }
            $value = sanitize_text_field( $value );
        }
        $key = sanitize_key( $ek_field_key );
        if ( '' === $key ) {
            continue;
        }
        update_post_meta( $event_id, 'event_field_' . $key, $value );
        $custom_field_keys[] = $key;
    }

    if ( ! empty( $custom_field_keys ) ) {
        update_post_meta(
            $event_id,
            'eventkoi_custom_fields_keys',
            array_values( array_unique( $custom_field_keys ) )
        );
    }
}, 10, 2 );
```

### What the handler does

| Action | Why |
|---|---|
| `post_type = eventkoi_event` | The EventKoi post type. |
| `post_status = draft` | Submission goes to admin review. Change to `pending` if you prefer the pending-review queue. |
| `date_type = standard` | Non-recurring event (recurring is out of scope — see the section below). |
| `standard_type = single` or `continuous` | `single` when the event starts and ends on the same calendar day; `continuous` when it spans multiple days. EventKoi uses this to decide how to render the date line on the public event page. |
| `event_days[]` | The structured date payload EventKoi reads. Times are **converted from the site timezone to UTC** and stored as ISO `2026-05-25T16:30:00Z`. |
| `start_date`, `end_date`, `start_timestamp`, `end_timestamp` | Denormalized companion fields. EventKoi's upcoming-index, the REST `orderby=start_date`, the admin Events table, and the dashboard upcoming-events widget all query these directly. **Always write them alongside `event_days`** — skipping them silently breaks every "next upcoming event" surface. |
| `timezone` | Stores the site timezone for downstream rendering. |
| `locations[]` | The structured location array. Only written if a venue name or address was provided. |
| `attendance_mode = none` | The event accepts no RSVPs or tickets. Change to `rsvp` or `tickets` if you want to default to one. |
| `wp_set_post_terms( … 'event_cal' )` | Assigns the event to the selected calendar. Without this the event won't appear in calendar-filtered views. |

### Timezone handling

The handler interprets the date and time the submitter entered **in your WordPress site's timezone** (`wp_timezone()` — set under Settings → General), then converts to UTC for storage. So with the site set to **Africa/Cairo** (UTC+3), a submission of `2026-05-25 19:30` is stored as `2026-05-25T16:30:00Z` and renders back as **7:30 pm** on the public event page.

This matches EventKoi's invariant: **dates are stored in UTC, rendered in `wp_timezone()`**.

---

## Step 3 — Embed the form

Create a new page (e.g. **Submit an Event**) and paste the shortcode:

```text
[gravityform id="1" title="false" description="false" ajax="true"]
```

Replace `id="1"` with your form ID. Publish the page.

---

## Step 4 — Test the flow

1. Visit the submission page logged out (or as a low-privilege user).
2. Fill in the form and submit.
3. In wp-admin → **EventKoi → Events** → filter by **Drafts**, you should see the new event.
4. Open the event in the EventKoi admin and confirm:
   - Title, description, dates, calendar are all populated correctly
   - The venue appears under **Location**
   - The date type is **Standard**

If anything is missing, check:

| Symptom | Likely cause |
|---|---|
| No draft event appears | Form ID mismatch — check `EKGF_FORM_ID` matches the form ID under Forms → All Forms. |
| Times are off by N hours | WordPress timezone is set to a UTC offset (e.g. `UTC+3`) instead of a named zone. Switch to a city-named timezone like `Africa/Cairo` under Settings → General. |
| Calendar isn't assigned | The Calendar dropdown's choice **values** must be term IDs, not term names. |
| Date looks wrong | Date field's format isn't set to `ymd` (YYYY-MM-DD). Check the Date field's Advanced tab. |

---

## Step 5 — Approve and publish

In **EventKoi → Events**:

1. Open the draft.
2. Review the title, description, date, location, and calendar.
3. Edit anything that needs adjustment.
4. Click **Publish**.

The event now appears on the public calendar, list views, query loops, and at `/event/{slug}/`.

---

## Variations

### All-day event

The All-day checkbox in the form already handles this. When checked, the handler:

- Ignores Start time and End time
- Stores `all_day = true` in the event day
- Anchors the day to `00:00:00` start and `23:59:59` end in the site timezone

### Virtual (online) event

Replace the venue fields in your form with a single **Meeting URL** field (let's say field ID `11`) and adjust the `locations` block in the handler:

```php
$virtual_url = esc_url_raw( (string) rgar( $entry, '11' ) );

if ( '' !== $virtual_url ) {
    update_post_meta(
        $event_id,
        'locations',
        array(
            array(
                'type'        => 'virtual',
                'name'        => 'Online',
                'virtual_url' => $virtual_url,
                'link_text'   => 'Join event',
            ),
        )
    );
}
```

### Featured image upload

Add a **File Upload** field (field ID `12`) restricted to images. After `wp_insert_post`:

```php
$urls = rgar( $entry, '12' );
$url  = is_array( $urls ) ? reset( $urls ) : $urls;

if ( $url ) {
    require_once ABSPATH . 'wp-admin/includes/media.php';
    require_once ABSPATH . 'wp-admin/includes/file.php';
    require_once ABSPATH . 'wp-admin/includes/image.php';

    $tmp = download_url( $url );
    if ( ! is_wp_error( $tmp ) ) {
        $file_array = array( 'name' => basename( $url ), 'tmp_name' => $tmp );
        $attach_id  = media_handle_sideload( $file_array, $event_id );
        if ( ! is_wp_error( $attach_id ) ) {
            set_post_thumbnail( $event_id, $attach_id );
            update_post_meta( $event_id, 'image', wp_get_attachment_url( $attach_id ) );
            update_post_meta( $event_id, 'image_id', $attach_id );
        }
    }
}
```

### Recurring events

Recurring events use a different storage shape (`date_type = recurring` plus a `recurrence_rules` array). They are intentionally out of scope for a public submission form — the rule shape is non-trivial and easy to fill out incorrectly. The recommended pattern: accept simple single/multi-day events through Gravity Forms, then let an admin convert to recurring inside the EventKoi editor when needed.

See the [Event Submission Field Reference](./event-submission-fields.md#5-recurring-event-rule-shape) for the recurring rule shape if you need to extend the handler.

---

## Custom fields

EventKoi lets you define your own fields under **Settings → Custom fields** — text, textarea, rich text, URL, radio, checkbox, dropdown. Once a custom field is defined there, you can expose it on the Gravity Form so the resulting event lands with your custom data already populated.

The handler in Step 2 already includes a `$custom_field_map` block. Wiring up a custom field is two changes: add the Gravity Forms input, then add one line to the map.

### 1 — Create the field in EventKoi

In wp-admin → **EventKoi → Settings → Custom fields → Add new**, set:

- **Field name** — the human label that renders on the public event page (e.g. `Cost`)
- **Field ID** — the slug stored in the database (e.g. `cost`). This is what you'll reference from the map.
- **Type** — text, textarea, rich text, URL, radio, checkbox, or dropdown
- For radio / checkbox / dropdown: enter the options, one per line

Create the field through this admin screen — not via direct database insert — so EventKoi normalises the `field_key` correctly. If the labels render as raw slugs (e.g. `cost: Free` instead of `Cost: Free`) on the public event page, that's the symptom of a malformed `field_key` row.

### 2 — Add the matching input to your form

In Forms → your form → Add field. Pick the Gravity Forms input that matches the EventKoi field type:

| EventKoi field type | Gravity Forms input | Stored value shape |
|---|---|---|
| Text | Single Line Text | string |
| Textarea | Paragraph Text | string |
| Rich text | Paragraph Text (HTML allowed) | HTML string |
| URL | Website / Single Line Text | URL string |
| Radio | Radio Buttons | string (the chosen option) |
| Checkbox (single) | Single Checkbox | `'1'` when checked, `''` when not |
| Checkbox (multi) | Checkboxes (multiple choices) | array of chosen option values |
| Dropdown | Drop Down | string (the chosen option) |

For radio / checkbox / dropdown the **value** of each choice in Gravity Forms must match the option string you typed in the EventKoi field settings — otherwise the value won't render.

Note the new Gravity Forms field ID (visible in the field's settings sidebar).

### 3 — Add one line to the handler's `$custom_field_map`

```php
$custom_field_map = array(
    11 => 'cost',         // GF field ID  =>  EventKoi field_key
    12 => 'dress_code',
);
```

That's it. The handler walks the map on every submission, sanitises each value (single string or array), writes `event_field_{field_key}` post meta, and appends to `eventkoi_custom_fields_keys` so EventKoi's editor recognises the event has custom data.

### Tip — pre-populate a Gravity Forms dropdown from a custom field's options

If your custom dropdown's options change over time, sync them into the Gravity Form so you don't keep two lists in sync by hand. Replace `<FORM_ID>` and `<GF_FIELD_ID>` to match your form, and `<EK_FIELD_KEY>` to the EventKoi field key whose options you want to mirror:

```php
add_filter( 'gform_pre_render_<FORM_ID>',       'ek_gf_inject_custom_field_choices' );
add_filter( 'gform_pre_validation_<FORM_ID>',   'ek_gf_inject_custom_field_choices' );
add_filter( 'gform_admin_pre_render_<FORM_ID>', 'ek_gf_inject_custom_field_choices' );

function ek_gf_inject_custom_field_choices( $form ) {
    global $wpdb;

    $row = $wpdb->get_row(
        $wpdb->prepare(
            "SELECT options FROM {$wpdb->prefix}eventkoi_fields WHERE field_key = %s AND status = 'active'",
            '<EK_FIELD_KEY>'
        )
    );
    if ( ! $row ) {
        return $form;
    }

    $decoded = json_decode( (string) $row->options, true );
    $options = isset( $decoded['options'] ) && is_array( $decoded['options'] ) ? $decoded['options'] : array();
    if ( empty( $options ) ) {
        return $form;
    }

    foreach ( $form['fields'] as &$field ) {
        if ( (int) $field->id !== <GF_FIELD_ID> ) {
            continue;
        }
        $field->choices = array_map(
            static fn( $opt ) => array( 'text' => $opt, 'value' => $opt ),
            $options
        );
    }
    return $form;
}
```

### How custom fields render on the front-end

You don't have to template anything — once `event_field_{field_key}` is set, EventKoi renders the field automatically. The label shown on the public event page comes from the field's **Field name** in Settings → Custom fields. Common ways to reference a custom field:

- **Block bindings** — bind any block's content attribute to `event_field_{field_key}` in the editor's bindings picker
- **Builder tokens** — use `{eventkoi_event_field_<field_key>}` in Beaver Builder, Bricks, Elementor, or Divi text fields
- **`event_custom_fields` token** — renders every populated custom field on the event in one block; useful as a fallback panel

See the [Event Submission Field Reference](./event-submission-fields.md) for the full token list and the bindings catalog.

---

## Security notes

- The handler runs whatever the submitter typed straight into `wp_insert_post`. If your form is **open to anonymous users**, treat every submission as untrusted:
  - We already sanitize: `wp_strip_all_tags` on the title, `wp_kses_post` on the description, `esc_url_raw` on URLs, `(int)` on calendar IDs.
  - Consider Gravity Forms' built-in **honeypot** and **reCAPTCHA / Cloudflare Turnstile** add-ons.
- Events are saved as `draft` so an admin always reviews before they go public.
- If you want only logged-in users (or specific roles) to submit, restrict the page or the form's confirmations under **Form Settings → Restrictions**.

---

## Reference: full field map

| Form input | GF field ID | EventKoi storage |
|---|---|---|
| Event title | `1` | `post_title` |
| Description | `2` | `post_content` + `description` meta |
| Start date | `3` | `event_days[0].start_date` (combined with `4`) |
| Start time | `4` | combined into `event_days[0].start_date` |
| End date | `5` | `event_days[0].end_date` (combined with `6`) |
| End time | `6` | combined into `event_days[0].end_date` |
| All-day | `7.1` | `event_days[0].all_day` |
| Venue name | `8` | `locations[0].name` |
| Venue address | `9` | `locations[0].address1` |
| Calendar | `10` | `event_cal` taxonomy term |
| — | — | `date_type = standard` |
| — | — | `standard_type = single` |
| — | — | `timezone` = site timezone |
| — | — | `attendance_mode = none` |

---

That's it — a public, admin-moderated event submission flow that produces correctly structured EventKoi events end-to-end.
