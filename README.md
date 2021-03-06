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

By default, only the two built-in messages classes of **updated** and **error** are allowed, but you can modify the array of allowed classes using the **flash_messages_allowed_classes** filter, like so:

```
function my_flash_classes($allowed_classes) {
    $allowed_classes[] = 'notice'; //adds 'notice' class to allowed array
    return $allowed_classes;
}
add_filter('flash_messages_allowed_classes', 'my_flash_classes');
```

If an invalid class name is used when queueing a message, the default class **updated** is used instead. Of course, you can also change this with a filter:

```
function my_flash_default_class($default_class_name) {
    return 'error'; //makes 'error' the default class name
}
add_filter('flash_messages_default_class', 'my_flash_default_class');
```