=== FG Drupal to WordPress ===
Contributors: Kerfred
Plugin Uri: https://wordpress.org/plugins/fg-drupal-to-wp/
Tags: drupal, importer, migration, cck, ubercart
Requires at least: 4.5
Tested up to: 6.6.1
Stable tag: 3.77.0
Requires PHP: 5.6
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Donate link: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=fred%2egilles%40free%2efr&lc=FR&item_name=fg-drupal-to-wp&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted

A plugin to migrate articles, stories, pages, categories, tags, images from Drupal to WordPress

== Description ==

This plugin migrates articles, stories, pages, categories, tags and images from Drupal to WordPress.

It has been tested with **Drupal 4, 5, 6, 7, 8, 9 & 10** and the latest version of WordPress. It is compatible with multisite installations.

Major features include:

* migrates the Drupal articles
* migrates the Drupal 6 stories
* migrates the Drupal basic pages
* migrates the Drupal categories
* migrates the Drupal tags
* migrates the Drupal images
* uploads all the posts media in WP uploads directories
* uploads external media (option)
* modifies the post content to keep the media links
* resizes images according to the sizes defined in WP
* defines the featured image to be the first post image (option)
* keeps the alt image attribute
* modifies the internal links
* compatible with the MySQL, PostgreSQL and SQLite Drupal database drivers

No need to subscribe to an external web site.

= Premium version =

The **Premium version** includes these extra features:

* migrates the comments
* migrates the authors
* migrates the administrators
* migrates the users
* migrates the custom post types
* migrates the custom taxonomies
* migrates the custom fields
* migrates the custom users fields
* migrates the users pictures
* migrates the navigation menus
* migrates the blocks as inactive widgets
* authenticates the users with their Drupal passwords
* SEO: redirects the Drupal URLs to the corresponding WordPress URLs
* ability to not import some data
* ability to import only specific node types
* imports and replaces the Image Assist shortcodes
* imports the images managed by the Image Attach Drupal module
* imports the nodes relationships
* imports the Drupal 8 Media entities
* imports the Drupal Media
* imports the Video Embed fields
* ability to run the import by WP CLI

The Premium version can be purchased on: [https://www.fredericgilles.net/fg-drupal-to-wordpress/](https://www.fredericgilles.net/fg-drupal-to-wordpress/)

= Add-ons =

The Premium version allows the use of add-ons that enhance functionality:

* CCK Custom Content Kit
* ECK Entity Construction Kit
* Meta tags
* Location custom fields
* Ubercart store
* Drupal Commerce store
* Name custom fields
* Addressfield custom fields
* Internationalization
* NodeBlock fields
* EntityReference relationships
* Media Provider (S3, SoundCloud, YouTube media)
* Forum
* Field collections
* Multifield
* Paragraphs
* Domain Access
* Countries
* Profile2 user fields
* Entity Embed
* Webform
* Book

These modules can be purchased on: [https://www.fredericgilles.net/fg-drupal-to-wordpress/add-ons/](https://www.fredericgilles.net/fg-drupal-to-wordpress/add-ons/)

== Installation ==

1.  Install the plugin in the Admin => Plugins menu => Add New => Upload => Select the zip file => Install Now
2.  Activate the plugin in the Admin => Plugins menu
3.  Run the importer in Tools > Import > Drupal
4.  Configure the plugin settings. You can find the Drupal database parameters in the Drupal file sites/default/settings.php<br />

== Screenshots ==

1. Parameters screen

== Translations ==
* English (default)
* French (fr_FR)
* other can be translated

== Frequently Asked Questions ==

= I get the message: "[fg-drupal-to-wp] Couldn't connect to the Drupal database. Please check your parameters. And be sure the WordPress server can access the Drupal database. SQLSTATE[28000] [1045] Access denied for user 'xxx'@'localhost' (using password: YES)" =

* First verify your login and password to the Drupal database.
If Drupal and WordPress are not installed on the same host:
* If you use CPanel on the Drupal server, a solution is to allow a remote MySQL connection.
 - go into the Cpanel of the Drupal server
 - go down to Database section and click "Remote MySQL"
 - There you can add an access host (WordPress host). Enter the access host as the SOME-WEBSITE-DOMAIN-OR-IP-ADDRESS and click add host.
* Another solution is to copy the Drupal database on the WordPress database:
 - export the Drupal database to a SQL file (with phpMyAdmin for example)
 - import this SQL file on the same database as WordPress
 - run the migration by using WordPress database credentials (host, user, password, database) instead of the Drupal ones in the plugin settings.

= I get this error when testing the connection: "SQLSTATE[HY000] [2002] Connection refused" or "SQLSTATE[HY000] [2002] No such file or directory" =

* This error happens when the host is set like localhost:/tmp/mysql5d.sock
Instead, you must set the host to be localhost;unix_socket=/tmp/mysql5d.sock

= The migration stops and I get the message: "Fatal error: Allowed memory size of XXXXXX bytes exhausted" or I get the message: “Internal server error" =

* First, deactivate all the WordPress plugins except the ones used for the migration
* You can run the migration again. It will continue where it stopped.
* You can add: `define('WP_MEMORY_LIMIT', '512M');` in your wp-config.php file to increase the memory allowed by WordPress
* You can also increase the memory limit in php.ini if you have write access to this file (ie: memory_limit = 1G). See the <a href="https://premium.wpmudev.org/blog/increase-memory-limit/" target="_blank">increase memory limit procedure</a>.

= The media are not imported =

* Check the URL field that you filled in the plugin settings. It must be your Drupal home page URL and must start with http:// or https://

= The media are not imported and I get the error message: "Warning: copy() [function.copy]: URL file-access is disabled in the server configuration" =

* The PHP directive "Allow URL fopen" must be turned on in php.ini to copy the medias. If your remote host doesn't allow this directive, you will have to do the migration on localhost.

= I get the message: "Fatal error: Class 'PDO' not found" =

* PDO and PDO_MySQL libraries are needed. You must enable them in php.ini on the WordPress host.<br />
Or on Ubuntu:<br />
sudo php5enmod pdo<br />
sudo service apache2 reload

= I get this error: PHP Fatal error: Undefined class constant 'MYSQL_ATTR_INIT_COMMAND' =

* You have to enable PDO_MySQL in php.ini on the WordPress host. That means uncomment the line extension=pdo_mysql.so in php.ini

= Does the migration process modify the Drupal site it migrates from? =

* No, it only reads the Drupal database.

= I get this error: Erreur !: SQLSTATE[HY000] [1193] Unknown system variable 'NAMES' =

* It comes from MySQL 4.0. It will work if you move your database to MySQL 5.0 before running the migration.

= I get this error "Parse error: syntax error, unexpected T_PAAMAYIM_NEKUDOTAYIM" =

* You must use at least PHP 5.3 on your WordPress site.

= I get this error: SQLSTATE[HY000] [2054] The server requested authentication method unknown to the client =

* It is a compatibility issue with your version of MySQL.<br />
You can read this post to fix it: http://forumsarchive.laravel.io/viewtopic.php?id=8667

= None image get transferred into the WordPress uploads folder. I'm using Xampp on Windows. =

* Xampp puts the htdocs in the applications folder which is write protected. You need to move the htdocs to a writeable folder.

= Do I need to keep the plugin activated after the migration? =

* No, you can deactivate or even uninstall the plugin after the migration (for the free version only).

= My screen hangs because of a lot of errors in the log window =

* You can stop the log auto-refresh by unselecting the log auto-refresh checkbox


Don't hesitate to let a comment on the [forum](https://wordpress.org/support/plugin/fg-drupal-to-wp) or to report bugs if you found some.

== Changelog ==

= 3.77.0 =
* New: Add the function get_node()
* Tested with WordPress 6.6.1

= 3.75.6 =
* Tested with WordPress 6.6

= 3.75.4 =
* Fixed: [ERROR] Error:SQLSTATE[42S22]: Column not found: 1054 Unknown column 'n.body' in 'field list'

= 3.75.3 =
* Fixed: With Drupal 4: Post body was empty
* Fixed: With Drupal 4: [ERROR] Error:SQLSTATE[42S22]: Column not found: 1054 Unknown column 'n.body' in 'field list'
* Fixed: With Drupal 4: Warning: Undefined array key "body_value"
* Tested with WordPress 6.5.4

= 3.75.1 =
* Fixed: Function register_taxonomy was called incorrectly. The "status" taxonomy "name" property (status) conflicts with an existing property on the REST API Posts Controller
* Tested with WordPress 6.5.3

= 3.75.0 =
* Fixed: Files whose filename is longer than 255 characters were not imported
* Fixed: Images were not imported by File System method

= 3.74.1 =
* Tested with WordPress 6.5.2

= 3.73.2 =
* Fixed: Pages, ACF post types and other post types not displayed (due to the "order" custom post type)

= 3.73.1 =
* Fixed: Translations missing
* Fixed: Deprecated: preg_match(): Passing null to parameter #2 ($subject) of type string is deprecated
* Fixed: Deprecated: strip_tags(): Passing null to parameter #1 ($string) of type string is deprecated
* Fixed: Deprecated: trim(): Passing null to parameter #1 ($string) of type string is deprecated
* Tweak: Replace rand() by wp_rand()
* Tested with WordPress 6.5

= 3.73.0 =
* Tweak: Replace file_get_contents() by wp_remote_get()
* Tweak: Replace file_get_contents() + json_decode() by wp_json_file_decode()
* Tweak: Replace json_encode() by wp_json_encode()
* Tweak: Remove the deprecated argument of get_terms() and wp_count_terms()

= 3.72.0 =
* Fixed: Unsafe SQL calls

= 3.71.0 =
* Fixed: Rename the log file with a random name to avoid a Sensitive Data Exposure

= 3.70.3 =
* Fixed: The media files with absolute path on a Drupal site located in a subdirectory were not imported

= 3.70.1 =
* Tested with WordPress 6.4.3

= 3.69.1 =
* Fixed: Pages not displayed because "year" is a reserved term and can not be used as a taxonomy

= 3.69.0 =
* New: Add the hook "fgd2wp_import_media_filename"
* New: Add the hook "fgd2wp_process_content_media_links_new_link"

= 3.68.0 =
* New: Don't import the images in duplicate
* Fixed: Plugin log can be deleted with a CSRF
* Fixed: Deprecated: preg_match_all(): Passing null to parameter #2 ($subject) of type string is deprecated

= 3.67.0 =
* New: Check if we need the ECK add-on (Drupal 8)

= 3.66.0 =
* Fixed: Wrong internal links modified
* Tested with WordPress 6.4.2

= 3.65.0 =
* New: Import the "image" post type as attachment
* New: Import the duplicate taxonomy terms

= 3.64.1 =
* Update the Help screen

= 3.64.0 =
* Tested with Drupal 10
* Tested with WordPress 6.4.1

= 3.63.5 =
* Tested with WordPress 6.4

= 3.63.4 =
* Tested with WordPress 6.3.2

= 3.63.1 =
* Fixed: TXT and PPS files were not imported
* Tested with WordPress 6.3.1

= 3.61.0 =
* New: Check if we need the Book add-on
* Tested with WordPress 6.3

= 3.60.1 =
* Fixed: "Type" and "terms" are reserved words for taxonomies

= 3.57.0 =
* New: Check if we need the Multifield add-on

= 3.56.0 =
* New: Add many hooks
* Fixed: FTP connection failed with password containing special characters
* Tested with WordPress 6.2.2

= 3.55.1 =
* Fixed: Fatal error: Uncaught TypeError: preg_match(): Argument #2 ($subject) must be of type string, array given

= 3.53.2 =
* Fixed: Notice: Function register_taxonomy was called incorrectly. The "content" taxonomy "name" property (content) conflicts with an existing property on the REST API Posts Controller.
* Tested with WordPress 6.2

= 3.53.0 =
* New: Import the "data-caption" image captions

= 3.52.3 =
* Fixed: Filenames containing % were not imported

= 3.52.1 =
* Fixed: Filenames containing &amp; were not imported

= 3.50.0 =
* New: Compatibility with PHP 8.2

= 3.47.4 =
* Fixed: The option "Import the media with duplicate names" didn't work anymore (regression from 3.44.0). So wrong images were imported.

= 3.46.0 =
* Tweak: Add the parameter $taxonomy in the hook "fgd2wp_get_node_taxonomies_terms"

= 3.45.3 =
* Fixed: Fatal error: Uncaught ArgumentCountError: Too few arguments to function _post_format_get_terms()
* Tested with WordPress 6.1.1

= 3.45.0 =
* Tested with WordPress 6.1

= 3.44.0 =
* Tweak: Shorten the filenames if the option "Import the media with duplicate names" is selected
* Fixed: Some posts had a wrong slug
* Tested with WordPress 6.0.3

= 3.42.0 =
* New: Add the functions "get_wp_post_ids_from_meta" and "get_wp_term_ids_from_meta"

= 3.41.0 =
* Tested with WordPress 6.0.2

= 3.37.2 =
* Fixed: With PostgreSQL: Warning: unserialize() expects parameter 1 to be string, resource given

= 3.37.0 =
* New: Add the hook "fgd2wp_map_taxonomy"

= 3.35.0 =
* New: Import the image "title" field of the featured images as image caption
* Tested with WordPress 6.0.1

= 3.34.0 =
* New: Check if we need the ECK add-on

= 3.33.0 =
* Fixed: Page 404 for the posts of type "author"
* Tweak: Rename the hook "fgd2wp_convert_node_type" to "fgd2wp_map_post_type"

= 3.31.0 =
* Tested with WordPress 6.0

= 3.29.0 =
* New: Add the "language" argument in the function get_node_slug()

= 3.28.0 =
* New: Add the WordPress path in the Debug Info
* Fixed: the Private key file field was displayed even when FTP is not chosen

= 3.27.0 =
* New: Connection through SFTP using a private key
* Tested with WordPress 5.9.3

= 3.26.1 =
* Fixed: Missing parent category

= 3.25.0 =
* New: Check if we need the Webform add-on

= 3.24.0 =
* New: Import the audio files in the post content

= 3.23.1 =
* Tweak: Add the function get_post_meta_like()

= 3.23.0 =
* Tweak: Refactor the JavaScript

= 3.22.0 =
* Tested with WordPress 5.9.2

= 3.19.1 =
* Fixed: Don't check if the CCK add-on is required on Drupal 7

= 3.18.0 =
* New: Don't delete the theme's customizations (WP 5.9) when removing all WordPress content
* Tested with WordPress 5.9

= 3.17.0 =
* New: Add the hook "fgd2wp_get_featured_image"
* Tested with WordPress 5.8.3

= 3.14.0 =
* Tested with WordPress 5.8.2

= 3.12.1 =
* Fixed: "[ERROR] Not a media" for HTML links

= 3.10.0 =
* New: Import the "post" post types
* Tested with WordPress 5.8.1

= 3.8.1 =
* Fixed: Images surrounded with a link were not imported in the content

= 3.6.0 =
* New: Add a spinner during the AJAX actions

= 3.4.3 =
* Fixed: Some variables were not escaped before displaying

= 3.4.1 =
* Fixed: Wrong plural terms
* Tested with WordPress 5.8

= 3.2.0 =
* New: Display the reference of the Drupal entity when a media can't be downloaded

= 3.1.0 =
* New: Add the hook "fgd2wp_modify_links_in_content"

= 3.0.4 =
* Fixed: Images containing spaces were not replaced in the post content

= 3.0.2 =
* New: Add the hook "fgd2wp_set_plugin_options"
* Tweak: Refactoring

= 3.0.0 =
* New: Add the "map_taxonomy" function
* New: Add the "fgd2wp_pre_dispatch" hook
* Tweak: Rename "convert_node_type" by "map_post_type"

...

= 2.0.0 =
* New: Add an help tab
* New: Add a debug info tab

...

= 1.0.0 =
* Initial version: Import Drupal articles, basic pages, categories, tags and images

== Upgrade Notice ==

= 3.77.0 =
New: Add the function get_node()
Tested with WordPress 6.6.1
