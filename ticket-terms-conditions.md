# EventKoi — Ticket Terms and Conditions

Where ticket terms and conditions are stored, where they display, and how to output them in your own templates.

Requires EventKoi 1.3.15.0 or later (works in both EventKoi Lite and Pro).

---

# Two levels of terms

| Level | Set in | Stored as | Shown |
| --- | --- | --- | --- |
| Per ticket type | Manage Tickets, on each ticket | `terms_conditions` column in the tickets table | Under that ticket's name and description in the purchase dialog |
| Event-wide | Ticket setup, one field per event | `tickets_terms_conditions` post meta on the event | Once at the bottom of the purchase dialog, above the checkout footer |

Use the event-wide field for general purchase terms ("All sales are final, no refunds after 7 days") and the per-ticket field for type-specific conditions ("VIP includes backstage access, ID required"). If both are set, both display.

Both fields accept basic HTML (sanitized with `wp_kses_post`).

---

# Showing terms in templates

The event-wide terms are available through the `[eventkoi]` data shortcode:

```text
[eventkoi data="tickets_terms_conditions"]
```

On a single event page the event is resolved from context automatically. Elsewhere, pass the event ID:

```text
[eventkoi id="123" data="tickets_terms_conditions"]
```

Output is wrapped in a `div.eventkoi-ticket-terms` element with paragraphs applied, so it can be styled with CSS:

```html
<div class="eventkoi-ticket-terms">
    <p>All sales are final. <strong>No refunds</strong> after 7 days.</p>
</div>
```

The shortcode prints nothing when the field is empty.

---

# Filters

Adjust the stored value before display:

```php
add_filter(
	'eventkoi_get_event_tickets_terms_conditions',
	function ( $terms, $event_id ) {
		return $terms;
	},
	10,
	2
);
```

Adjust the rendered HTML of the shortcode output:

```php
add_filter(
	'eventkoi_rendered_tickets_terms_conditions',
	function ( $output, $event_id ) {
		return $output;
	},
	10,
	2
);
```
