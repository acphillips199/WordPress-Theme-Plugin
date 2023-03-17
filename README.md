# WordPress-Theme-Plugin
Custom WordPress Theme:

Create a new folder in the "wp-content/themes" directory of your WordPress installation and name it whatever you want your theme to be called.
Create a new file in that folder called "style.css" and add the following code:

/*
Theme Name: Your Theme Name
Theme URI: http://your-theme-uri.com/
Author: Your Name
Author URI: http://your-author-uri.com/
Description: A brief description of your theme
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Tags: responsive-layout, custom-colors, custom-logo
*/


Create a new file in the same folder called "index.php" and add the following code:

<?php get_header(); ?>
<main>
  <!-- Your main content goes here -->
</main>
<?php get_footer(); ?>


Create a new file in the same folder called "functions.php" and add any additional functions or customizations that you want to add to your theme. For example:


// Add support for custom menus
function register_my_menus() {
  register_nav_menus(
    array(
      'primary-menu' => __( 'Primary Menu' ),
      'footer-menu' => __( 'Footer Menu' )
    )
  );
}
add_action( 'init', 'register_my_menus' );

// Add support for custom logo
function custom_theme_setup() {
  add_theme_support( 'custom-logo', array(
    'height'      => 100,
    'width'       => 400,
    'flex-width'  => true,
    'flex-height' => true
  ) );
}
add_action( 'after_setup_theme', 'custom_theme_setup' );


Custom WordPress Plugin:

Create a new folder in the "wp-content/plugins" directory of your WordPress installation and name it whatever you want your plugin to be called.
Create a new file in that folder called "plugin-name.php" and add the following code:


<?php
/**
 * Plugin Name: Plugin Name
 * Plugin URI: http://your-plugin-uri.com/
 * Description: A brief description of your plugin
 * Version: 1.0
 * Author: Your Name
 * Author URI: http://your-author-uri.com/
 * License: GPL2
 */

// Your plugin code goes here


Add any additional functions or customizations that you want to add to your plugin. For example:

// Add a shortcode for displaying the current date
function display_current_date() {
  $date = date( 'F j, Y' );
  return '<p>Today\'s date is ' . $date . '</p>';
}
add_shortcode( 'current_date', 'display_current_date' );

// Add a custom post type for portfolio items
function create_portfolio_post_type() {
  register_post_type( 'portfolio',
    array(
      'labels' => array(
        'name' => __( 'Portfolio' ),
        'singular_name' => __( 'Portfolio Item' )
      ),
      'public' => true,
      'has_archive' => true,
      'supports' => array( 'title', 'editor', 'thumbnail' ),
      'taxonomies' => array( 'category', 'post_tag' )
    )
  );
}
add_action( 'init', 'create_portfolio_post_type' );


