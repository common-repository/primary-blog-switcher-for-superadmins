=== Primary Blog Switcher for SuperAdmins ===
Contributors: dsader
Donate link: http://dsader.snowotherway.org
Tags: multisite, network, primary blog, primary site, profile, my blogs, primary blog switcher, edit users,
Requires at least: 3.0
Tested up to: 4.6
Stable tag: Trunk
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

WordPress multisite network plugin to allow Network Admin to set the "Primary Blog" (aka Primary Site) of a user while editing a profile.

== Description ==
WordPress [Multisite](http://codex.wordpress.org/Create_A_Network) network plugin to allow Network Admin to set the "Primary Blog" (aka Primary Site) of a user while editing a user's profile.

Well, for whatever reasons (usually users fiddling around - I use WP multisite in a school with students grades 4-12), users aren't attached(or become unattached) to the correct "Primary Blog". 

This isn't a deal breaker, but annoying when they login and are redirected to a blog that is not their expected primary. It also is annoying when I use other plugins to list user primary blog for display in a member directory, member profiles, etc.

Telling users to reset their primary blog at their own Dashboard->My Blogs is a fix, but the SuperAdmin(Teacher in my case) can head off the confusion first with this plugin. There is no other way(AFAIK) for the Network Admin to set the "Primary Blog" of a user while editing their profile. 

Now, I can quickly scan the Network Admin list of users and edit profiles and set primary blogs of any user correctly.

I can also use my <a href="http://wordpress.org/extend/plugins/menus/">Menus plugin</a> to toggle the My Sites menu item so users can no longer fiddle with the Primary Site switcher at all. Problem solved.

== Installation ==

This section describes how to install the plugin and get it working.

1. Upload the plugin to your blog, Network Activate it
2. Edit user profiles as Network Dashboard->Users->Edit
3. View Network Dashboard for notices of users who have the main blog set as their primary blog, or no blog at all.

== Frequently Asked Questions ==

* Can I set the Main blog as a user's primary? Yes.

* Can I set the Dashboard blog (if enabled) as a user's primary? Yes.

* Can I set Donncha's Sitewide Tags blog (if enabled) as a user's primary? Yes.

* Can I add a user to some other blog "special blog" as their primary? Yes, but see "special blog" comments in the plugin code.

* Does this plugin filter the list of blogs already listed at a user's Dashboard->My Sites->Primary Site? No.

* I can't change a user's primary blog, there are no blogs to choose from in the dropdown on their profile? Add the user first to a couple of blogs and try again.

== Screenshots ==


== Notes ==

The original code for the Primary Site switcher is in wp-admin-includes/ms.php. I've basically copied that, but changed `get_current_user_id()` to `$edit_user = (int) $_GET['user_id'];` and added it to the "edit_user_profile" hook.

The plugin can be used to add users to a "Special Blog" by uncomment(remove the /* and */) this section in the plugin code and change the $special_blog_id:
`
<optgroup label="Other Blogs"></optgroup>
<optgroup label="Special Blog">
<?php $special_blog_id = '63'; //
$special_blog = get_blog_details( $special_blog_id ); ?>
<option value='<?php echo $special_blog_id ?>'>http://<?php echo $special_blog->domain.$special_blog->path ?></option>
</optgroup>
`

== Changelog ==
= 4.6 =
* WP 4.6 tests OK, cleanup php notices

== Upgrade Notice ==

= 4.6 =
* WP 4.6 tests OK, cleanup php notices

