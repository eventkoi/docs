# EventKoi — RSVP Custom Fields

Add your own fields to the RSVP form (for example a first/last name split, a phone number, or a dietary preference) with a small code snippet. No template overrides needed.

Requires EventKoi 1.3.15.0 or later.

---

# How it works

EventKoi exposes three hooks:

| Hook | Type | Purpose |
| --- | --- | --- |
| `eventkoi_rsvp_fields` | filter | Register extra fields shown in the RSVP form |
| `eventkoi_rsvp_show_name_field` | filter | Hide the built-in Name input (e.g. when you replace it with first/last name fields) |
| `eventkoi_rsvp_payload` | filter | Adjust the final RSVP data right before it is saved |

Registered fields are rendered automatically in the RSVP dialog, validated on the server, stored with the RSVP, shown when an attendee edits their RSVP, returned by the RSVP admin API, and included as extra columns in the CSV export.

Where to put the snippets: a small custom plugin, your child theme's `functions.php`, or a code snippets plugin.

---

# Field options

Each field is an array with these keys:

| Key | Required | Description |
| --- | --- | --- |
| `key` | yes | Unique identifier, lowercase letters/numbers/underscores. Cannot be `name`, `email`, `status`, or `guests`. |
| `label` | yes | Label shown above the input and used as the CSV column header. |
| `type` | no | One of `text` (default), `email`, `tel`, `number`, `textarea`, `select`, `checkbox`. |
| `required` | no | Set `true` to require a value. Validated in the browser and on the server. |
| `options` | for `select` | Array of allowed choices. Submissions outside this list are discarded. |
| `placeholder` | no | Placeholder text for the input. |

The filter also receives the event ID as a second argument, so you can register different fields per event.

---

# Example: split Name into First name and Last name

```php
add_filter(
	'eventkoi_rsvp_fields',
	function ( $fields ) {
		$fields[] = array(
			'key'      => 'first_name',
			'label'    => 'First name',
			'type'     => 'text',
			'required' => true,
		);
		$fields[] = array(
			'key'      => 'last_name',
			'label'    => 'Last name',
			'type'     => 'text',
			'required' => true,
		);
		return $fields;
	}
);

// Hide the built-in single Name field.
add_filter( 'eventkoi_rsvp_show_name_field', '__return_false' );
```

That is all you need. When the built-in Name field is hidden and `first_name` / `last_name` fields exist, EventKoi automatically composes the stored attendee name as "First Last", so check-in, emails, the admin list, and exports keep working as before. For logged-in users, both fields are prefilled from their WordPress profile.

---

# Example: extra fields (phone and meal choice)

```php
add_filter(
	'eventkoi_rsvp_fields',
	function ( $fields ) {
		$fields[] = array(
			'key'         => 'phone',
			'label'       => 'Phone number',
			'type'        => 'tel',
			'placeholder' => '+1 555 000 0000',
		);
		$fields[] = array(
			'key'      => 'meal',
			'label'    => 'Meal preference',
			'type'     => 'select',
			'required' => true,
			'options'  => array( 'Standard', 'Vegetarian', 'Vegan' ),
		);
		return $fields;
	}
);
```

---

# Example: fields for one event only

```php
add_filter(
	'eventkoi_rsvp_fields',
	function ( $fields, $event_id ) {
		if ( 123 === $event_id ) {
			$fields[] = array(
				'key'   => 'company',
				'label' => 'Company',
			);
		}
		return $fields;
	},
	10,
	2
);
```

---

# Example: post-process the RSVP before saving

`eventkoi_rsvp_payload` runs after validation, right before the RSVP is stored. It receives the prepared payload and the raw request data.

```php
add_filter(
	'eventkoi_rsvp_payload',
	function ( $payload ) {
		// Store the name as "Last, First" instead of the default "First Last".
		if ( ! empty( $payload['fields']['first_name'] ) && ! empty( $payload['fields']['last_name'] ) ) {
			$payload['name'] = $payload['fields']['last_name'] . ', ' . $payload['fields']['first_name'];
		}
		return $payload;
	}
);
```

---

# Where the data goes

- Custom values are stored as JSON in the `meta` column of the `wp_eventkoi_rsvps` table, under the `fields` key.
- The RSVP admin endpoint (`GET /eventkoi/v1/rsvps`) returns them on each row as `fields`.
- The CSV export (`GET /eventkoi/v1/rsvps/export`) adds one column per registered field, labeled with the field's `label`.
- When an attendee re-opens the RSVP dialog (via their check-in link or while logged in), their previous values are prefilled.

# Notes

- Only registered fields are saved. Unknown keys submitted to the API are discarded.
- Values are sanitized by type on the server (`email` via `sanitize_email`, `select` against the `options` list, and so on).
- Required fields return a clear error ("Last name is required.") if missing, both in the form and from the REST API.
