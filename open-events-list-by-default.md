# EventKoi — Open the Events List by Default in WP Admin

Some sites may want the main **EventKoi** admin menu item to open the event list immediately, instead of opening the EventKoi dashboard.

This does not require changing EventKoi. You can add a small custom snippet to the site.

---

# What this does

- Clicking the main **EventKoi / Events** menu item opens:

```text
wp-admin/admin.php?page=eventkoi#/events
```

- The **Dashboard** submenu item remains visible.
- The Dashboard page still works when opened directly.
- Other EventKoi admin pages are not redirected.

---

# Code snippet

Add this to a small custom plugin, an MU plugin, or a trusted code snippets plugin.

```php
/**
 * EventKoi: open Events list when clicking the main admin menu item.
 */
add_action(
	'admin_head',
	function () {
		$events_url = admin_url( 'admin.php?page=eventkoi#/events' );
		?>
		<script>
		(function () {
			if (window.location.search.indexOf('page=eventkoi') === -1) return;

			var hash = window.location.hash || '';

			// Only redirect the bare EventKoi admin URL.
			// Do not redirect #/dashboard, so the Dashboard submenu still works.
			if (!hash || hash === '#' || hash === '#/') {
				window.location.replace(<?php echo wp_json_encode( $events_url ); ?>);
			}
		})();
		</script>
		<?php
	},
	1
);

add_action(
	'admin_footer',
	function () {
		$events_url = admin_url( 'admin.php?page=eventkoi#/events' );
		?>
		<script>
		(function () {
			var menu = document.getElementById('toplevel_page_eventkoi');
			if (!menu || !menu.children.length) return;

			var topLink = menu.children[0];
			if (topLink && topLink.tagName === 'A') {
				topLink.href = <?php echo wp_json_encode( $events_url ); ?>;
			}
		})();
		</script>
		<?php
	},
	100
);
```

---

# Why JavaScript is used

EventKoi’s admin uses hash routes such as:

```text
#/dashboard
#/events
#/settings
```

The hash portion of a URL is handled in the browser and is not sent to PHP. Because of that, PHP alone cannot reliably redirect from the dashboard route to the events route.

The snippet uses a small amount of admin JavaScript to:

1. Change the main EventKoi menu link to `#/events`.
2. Redirect only the bare EventKoi admin URL to `#/events`.

---

# Removing the customization

To restore the default EventKoi behavior, remove the snippet.
