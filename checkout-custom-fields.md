# EventKoi — Checkout Custom Fields

Add your own fields to the ticket checkout form (company name, phone, meal choice, and so on) with a small code snippet. No template overrides needed.

Requires EventKoi 1.3.15.0 or later (works in both EventKoi Lite and Pro). For RSVP forms, see [RSVP Custom Fields](./rsvp-custom-fields.md).

---

# How it works

Register fields with the `eventkoi_checkout_fields` filter. They render in the checkout step of the ticket purchase dialog, after the built-in First name / Last name / Email inputs, and are validated in the browser and on the server.

Note: checkout already collects first and last name as separate fields by default, so unlike RSVP there is no name-splitting needed here.

```php
add_filter(
	'eventkoi_checkout_fields',
	function ( $fields ) {
		$fields[] = array(
			'key'      => 'company',
			'label'    => 'Company name',
			'type'     => 'text',
			'required' => true,
		);
		$fields[] = array(
			'key'      => 'meal',
			'label'    => 'Meal preference',
			'type'     => 'select',
			'options'  => array( 'Standard', 'Vegetarian', 'Vegan' ),
		);
		return $fields;
	}
);
```

Field options are the same as RSVP custom fields:

| Key | Required | Description |
| --- | --- | --- |
| `key` | yes | Unique identifier, lowercase letters/numbers/underscores. Cannot be `first_name`, `last_name`, `email`, or `checkout_note`. |
| `label` | yes | Label shown above the input and on the order. |
| `type` | no | One of `text` (default), `email`, `tel`, `number`, `textarea`, `select`, `checkbox`. |
| `required` | no | Set `true` to require a value before checkout can start. |
| `options` | for `select` | Array of allowed choices. Submissions outside this list are discarded. |
| `placeholder` | no | Placeholder text for the input. |

The filter receives the event ID as a second argument for per-event fields:

```php
add_filter(
	'eventkoi_checkout_fields',
	function ( $fields, $event_id ) {
		if ( 123 === $event_id ) {
			$fields[] = array(
				'key'   => 'badge_name',
				'label' => 'Name on badge',
			);
		}
		return $fields;
	},
	10,
	2
);
```

---

# Where the data goes

**Pro (native Stripe checkout):** values are attached to the order as notes once payment confirms. Each field becomes a "Checkout field" entry in the order's activity feed in the EventKoi admin, formatted as `Label: value`.

**Lite and Pro with WooCommerce checkout:** values are saved on the WooCommerce order as the `_eventkoi_checkout_fields` order meta, and each field is also added as a WooCommerce order note (`Label: value`), visible in the WooCommerce order screen.

Only registered fields are saved; unknown keys submitted to the API are discarded, and values are sanitized by type on the server. A missing required field blocks the checkout with a clear error ("Company name is required.") before any payment session is created.
