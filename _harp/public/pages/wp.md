Cuberis primarily uses [WordPress](https://wordpress.org/) to create fantastic and robust websites. Below outlines our approach to development for WordPress.

## Themes
The [Cuberis Base](https://github.com/cuberis/cuberis-base) theme is a modern WordPress starter theme built on top of [Sage](https://github.com/roots/sage) (specifically, the version 8.x branch) and modified to our project and development processes. Some areas of interest are a streamlined build process for assets through [Laravel Mix](https://github.com/JeffreyWay/laravel-mix) and versioned dependency management with [Composer](https://getcomposer.org/) and [npm](https://www.npmjs.com/).

The theme's main repository (private, requires access to our organization) can be found on GitHub with additional information on getting started: https://github.com/cuberis/cuberis-base

## Plugins
Cuberis embraces a minimalistic approach to the use of plugins. If functionality can easily be built into the theme, that is preferrable to installing extra plugins. Plugins with ample documentation, frequent update cycles, and flexible APIs are preferred. For more complicated functionality or enhancements, there are several plugins that are used within nearly every project including:

* Advanced Custom Fields PRO
* Gravity Forms
* Yoast SEO

## Best Practices
While this is not an all-compassing list of best practices Cuberis follows when it comes to developing for WordPress, this section serves as a good jumping off point with lessons learned and examples.

### wp-config
When developing for WordPress, always use Debug mode by setting `define( 'WP_DEBUG, true );` in your `wp-config.php`. On the same note, be sure to set this constant to `false` on production. Some other sensible defaults to consider for your project are:

```
/**
 * Allows for granular control over logic within the theme for different server environments (this is a custom constant).
 */
define( 'WP_ENV', 'your_environment_name' ); // examples: 'production', 'dev'

/**
 * Limits the number of revisions WordPress will store. By default, WordPress will store an infinite number of revisions on each post.
 */
define( 'WP_POST_REVISIONS', 5 );

/**
 * Turn off the Theme & Plugin editors as a recommended security measure. Even WordPress discourages their usage.
 * @source https://codex.wordpress.org/Hardening_WordPress#Disable_File_Editing
 */
define( 'DISALLOW_FILE_EDIT', true );
```

### Don't Repeat Yourself (DRY) ☔️
At Cuberis, we make a great effort to conform to the **DRY** principle. This means if there is ever a case when, you are copying and pasting the same code between multiple templates or functions, you are not being DRY! By adhering to the DRY principle, we ensure that our code is cleaner, more readable and most importantly, easier to update and maintain.

### Query Performance & Considerations
Posts should never be queried directly by their ID. Over time, content changes on a WordPress site and the ID becomes an unrelyable way to query a post. Depending on your use case, consider setting up an ACF Theme Options page to set a page for a specific purpose.

```
// No
$my_custom_404_page = get_post(404);

// Yes
$my_custom_404_page = get_field('custom_404_page', 'option');
```

To improve query performance, only return what you need. For example, the following arguments would only return an array of post IDs and removes pagination.

```
$items = get_posts([
  'fields'        => 'ids',
  'no_found_rows' => true
]);
```

Other recommendations:
* Avoid using `posts_per_page => -1`.
* Avoid querying the database directly unless absolutely necessary. Use standard WordPress conventions such as `WP_Query` or `get_posts()`.
* Try to remove as much logic from WordPress templates—such as modifying the default query on an archive template using the `pre_get_posts` filter.

### Leverage Native WordPress APIs
The contributors of WordPress couldn't have said it any better...

Using the core APIs when developing for WordPress is strongly encouraged because:

* Core APIs make building things for WordPress easier by providing hooks, actions, filters, helper functions.
* WordPress does the “heavy lifting” for you (database calls, input validation, security, form building) so you don’t have to.
* Using core APIs ensures your code will be both backward-compatible and future-proof.
* The APIs allow seamless integration into wp-admin for plugin/theme options pages, inline help documentation, etc.

Source: https://make.wordpress.org/core/handbook/best-practices/core-apis/

A few exceptions to note:
* We prefer to use Advanced Custom Fields over the [Custom Fields](https://codex.wordpress.org/Custom_Fields) API.
* Generally speaking, we avoid [Widgits](https://codex.wordpress.org/WordPress_Widgets) as there are more modern and conventional ways to add custom content and features to sites.
* [Shortcodes](https://codex.wordpress.org/Shortcode_API) are fine but should only be used unless absolutely necessary.
