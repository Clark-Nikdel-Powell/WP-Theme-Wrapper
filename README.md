# WP-Theme-Wrapper
A wrapper function that intercepts WordPress' `template_include` function, allowing us to use base.php instead.

Say you've got two template files for a post type, `archive-book.php` and `single-book.php`. The way that WordPress normally works, you'd have to repeat at least `get_header()` and `get_footer()` in each of these files. Perhaps there's more structural HTML to it. The trouble is, now you have some amount of duplicated code that is not specific to the layout.

The WP Theme Wrapper functions intercept WordPress template selection. Every template uses `base.php`. It then takes the file that _would_ have been selected and puts it _into_ `base.php`. This way, `archive-book.php` and `single-book.php` only have markup that is specific to the specific view and nothing more.

This also helps us visualize how the template files fit together from start to end; that is, we're not splitting open and close div tags across multiple PHP files.

**Note:** normally, we don't resort to using a WordPress template file, because doing this also overrides `index.php`, The Loop, and all the theme Actions that we've placed around The Loop. You can probably achieve the same effect by using a file structure like `ui/book/book-content-archive.php` and `ui/book/book-content-singular.php`. 

#### Reference
- [March 10, 2017 - Centralizing WordPress Code with a Theme Wrapper, Custom Actions and Layout Classes](https://pagely.com/blog/centralizing-wordpress-code-with-a-theme-wrapper-custom-actions-and-layout-classes/)
