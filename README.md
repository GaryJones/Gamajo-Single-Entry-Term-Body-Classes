# Gamajo Single Entry Term Body Classes

A class to copy into your WordPress plugin, to make adding taxonomy-term HTML classes to single custom post type entries considerably easier.

## Description

When displaying a single custom post type entry, some may want to style it according to the terms of a particular taxonomy that are applied to it. One method is by adding extra values to the body classes on that single entry.

This class makes adding them trivially easy in just a few lines of code.

## Installation and Usage

This isn't a WordPress plugin on its own, so the usual instructions don't apply. Instead:

1. Copy [`class-gamajo-single-entry-term-body-classes.php`](class-gamajo-single-entry-term-body-classes.php) into your plugin. It can be into a file in the plugin root, or better, an `includes` directory.
2. Within your plugin files, most likely as a standalone snippet in the main plugin file, implement something like:

~~~php
if ( ! is_admin() ) {
  if ( ! class_exists( 'Gamajo_Single_Entry_Term_Body_Classes' ) ) {
    require plugin_dir_path( __FILE__ ) . 'includes/class-gamajo-single-entry-term-body-classes.php';
  }
  $your_plugin_body_classes = new Gamajo_Single_Entry_Term_Body_Classes;
  $your_plugin_body_classes->init( 'your-cpt' );
}
~~~

That's it!

## Notes

If you have a term of `step-mother` in a taxonomy of `family` applied to your single custom post type entry, then a body class of `family-step-mother` will be applied. This repeats for all terms on all taxonomies applied to the entry.

Class values will be lowercase, with underscores replaced with hyphens, before being sanitized with `sanitize_html_class()` which strips out any `%`-encoded octets and limits the remaining value to `A-Za-z0-9_-`.

The WordPress functions used in this class mean it can be used in WordPress 2.8.0 or later, which is when the `body_class` filter was added.

## Contributions

Contributions are welcome - fork, fix and send pull requests against the `develop` branch please.

## License

GPL-2.0+, so feel free to use in any WordPress project. Let me know when you do (not a requirement of usage) as I'd love to know where my code is being used!

## Credits

Built by [Gary Jones](https://twitter.com/GaryJ)  
Copyright 2014 Gary Jones, [Gamajo Tech](http://gamajo.com/)
