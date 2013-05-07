wp-flash-messages
=================

Simple flash message functionality for your WordPress plugin.

Use the function **queue_flash_message()** to enqueue a flash message that will be displayed on the next admin page load.

**queue_flash_message()** takes the following form:

```
<?php queue_flash_message( $message, $class = 'updated' ); ?>
```

The two parameters are:

- **$message** - The string to be displayed. HTML is okay, but keep in mind that your $message will be wrapped in a **p** and a **div** tag. (See output example below.)
- **$class** - the CSS class to be applied to the div element.

The output will look like this:

```
<div class="$class">
	<p>$message</p>
</div>
```

*This is the same markup that WordPress generates for its own flash messages.*
