== Changelog ==

= v2.0.3 - 2016/02/12 =
-----------------------

+ Removed an unsed quiz stub


= v2.0.2 - 2016/02/11 =
-----------------------

+ Bugfix: removed a progressive syntax array that caused fatal errors on older versions of PHP


= v2.0.1 - 2016/02/11 =
-----------------------

##### Updated General Settings Screen

+ Improved the general settings interface to be more visually appealing and to provide some ad space to alert customers to other LifterLMS products and information.
+ Moved Currency options to the Checkout settings screen

##### Bug Fixes

+ Properly initialized jQuery on the vouchers metabox admin scripts
+ removed some php shortcut echos (`<?= $var; ?>`)
+ Resolve issue where courses that are available with a membership or on it's own outside of the membership would prevent users from accessing content if they were not a member.
+ Fixed a few files where undefined variables were being referenced and generating php notices
+ removed an call to a WordPress core function that has never existed. Not sure what we were thinking there...

###### Enhancements

+ Updated CSS to provide better course syllabus layout on smaller screens
+ Added validation to prevent against duplicate voucher code creation

= v2.0.0 - 2016/02/04 =
-----------------------

##### Auto-advancing lessons

+ We've heard your feedback and added a new global course option which will auto-advance a student to the next lesson upon lesson completion.

##### Bug Fixes

+ Added spaces between numbers and "of" on the counter for course syllabus templates
+ Removed a template hook that was creating duplicate lesson thumbnails on quite a few themes

##### Membership Admin Improvements

Visit the "Enrollment" tab on any membership to see some new additions to make managing your memberships easier.

+ You can now add courses to and remove courses from a Membership from the Membership itself
+ You can now opt to automatically enroll students in a course (or multiple courses) when they sign up for a membership by checking "Auto Enroll" next to the course on the Membership enrollment tab

##### Student Enrollment & Removal on Courses Admin Screen

We've updated the Students tab interface for performance and usability!

+ AJAX enabled searching by student name and or email
+ Increased performance for course page load by only calling student information when needed. This resolves a bug identified by users with large user databases and/or low-powered servers.
+ Allow for addition or removal of several students at a time.

##### Syllabus Template

+ Added a Course setting to optionally enable Lesson Thumbnails on the Course Syllabus
+ Added a Course setting Display greyed out lesson completion checkmark icons on lessons not competed in the course syllabus
+ Rewored CSS on the course syllabus to rely on floats rather than absolute positioning, should allow for more robust custimization with less frustration
+ Refactored the syllabus template at "templates/course/syllabus.php" for better performance and readability

##### Updates and enhancements

+ User email is now displayed on the "Students" table on student analytics screens
+ Membership now has it's own admin menu
+ Reordered the LifterLMS admin menu and submenu items
+ Removed membership specific taxonomies from courses
+ Removed course specific taxonomies from memberships
+ Coupon code is now a required field when creating a coupon
+ "Humbled" the metabox on all post types that restricts the post to a membership. The metabox would previously gain priority over the WordPress publishing actions metabox. The priority has been reduced to "default" and will to fall into line with all other metaboxes on the screen and appear based on registration priority. If you can't find the metabox, SCROLL DOWN! If you want to put it back up on the top, you can simply drag it up there and WordPress will save your preference.

##### Deprecated Classes

We've added a "deprecated" file which holds a few stubs for classes and functions deprecated below as to prevent fatal errors. The functions and classes in the deprecated class are classes which we know are being utilized by approved LifterLMS extensions and will allow users to upgrade LifterLMS without upgrade extensions without breaking their websites!

+ `LLMS_Activate` which as previously used to activate the plugin for updates via the LifterLMS Update Server and is no longer required.
+ PUC (plugin update checker) Library has been completely removed as it is no longer required for plugin updates.
+ `LLMS_Analytics_Dashboard` was removed as it was a stub that was never used and shouldn't have ever been released as a part of the LifterLMS codebase. I can't believe no one reported this bug!

##### Deprecated Functions

+  `lifterlms_template_section_syllabus()`

**The following are officiallby deprecated and removed to prevent WooCommerce compatibility conflicts**

+ `is_shop()` replaced by `is_llms_shop()`
+ `is_account_page()` replaced by `is_llms_account_page()`
+ `is_checkout()` replaced by `is_llms_checkot()`


##### Deprecated Templates

+ templates/course/section_syllabus.php

##### New Account Dashboard Filters

*[View documentation for more information](https://lifterlms.readme.io/docs/filters-account)*

+ `lifterlms_account_greeting`
+ `lifterlms_my_courses_title`
+ `lifterlms_my_courses_enrollment_status_html`
+ `lifterlms_my_courses_start_date_html`
+ `lifterlms_my_courses_course_button_text`
+ `lifterlms_my_certificates_title`

##### New Checkout Page Filters:

*[View documentation for more information](https://lifterlms.readme.io/docs/filters-checkout)*

+ `lifterlms_checkout_user_logged_in_output`
+ `lifterlms_checkout_user_not_logged_in_output`

##### New Course Filters:

*[View documentation for more information](https://lifterlms.readme.io/docs/filters-course)*

+ `lifterlms_product_purchase_account_redirect`
+ `lifterlms_product_purchase_redirect_membership_required`
+ `lifterlms_product_purchase_checkout_redirect`
+ `lifterlms_product_purchase_membership_redirect`
+ `lifterlms_lesson_complete_icon`






= v1.5.0 - 2016/01/22 =
-----------------------

##### WooCommerce Integration Enhancements

__NOTE: The following enhancements only apply when the WooCommerce Integration is enabled__

**Always redirect to the WooCommerce Cart when a SKU Matched Product can be found**

+ LifterLMS Products (courses and memberships) which are SKU matched to a WooCommerce product will now automatically add the related WooCommerce product to the WooCommerce shopping cart and then automatically redirect the visitor to the WooCommerce cart when the visitor attempts to enroll in a course or membership from the LifterLMS course or membership page.
+ If no WooCommerce product is found via a SKU match, the user will proceed to the LifterLMS checkout.
+ This will enable you to determine which Cart you want a user to use on a product by product basis. You may sell certain courses via WooCommerce and others via LifterLMS (should you choose to do so).

**Multiple Item Checkout**

+ When a WooCommerce order is complete user's will now be automatically enrolled in **all** courses and/or memberships in the WooCommerce order. This improves upon a previously limitation that would only allow WooCommerce checkout with one LifterLMS product at a time.
+ The products in the order will be intelligently SKU matched to LifterLMS Courses or Memberships.
+ You may also mix and match between WooCommerce products matched to LifterLMS products and those which are not matched to LifterLMS products. For example, your customers may now buy a Course via SKU matching as well as a T-Shirt that is not matched to a LifterLMS course via a SKU.

##### Other Fixes and improvements

+ Fixed a bug that caused quiz results to display for users who had never taken the quiz.
+ Added Wistia as an oEmbed provider to fix an issue related to default oembed handling in WordPress 4.4.
+ added a `.cc_cvv` class that mimics the existing `#cc_cvv` styles to allow gateway extensions to change the ID of the field in their credit card forms
+ Added support for new 1.4.5 capability fixes to be also be reflected under the "+New" menu item in the WP Admin Bar. There are no changes to the filters, the capability filters will simply also remove restricted post types from the admin bar now (as they should).
+ Tested and compatible up to WordPress 4.4.1

##### Deprecations

**The following functions have been staged for deprecation in LifterLMS 2.0!**

+ Setup the `is_account_page()` function to be replaced by `is_llms_account_page()` function. The original causes conflicts when WooCommerce is installed as WooCommerce includes a core function by the same name. All references to `is_account_page()` in LifterLMS have been removed and the original has been left to prevent issues with developers currently relying on the LifterLMS version of thefunction.
+ Setup the `is_checkout()` function to be replaced by `is_llms_checkout()` function. The original causes conflicts when WooCommerce is installed as WooCommerce includes a core function by the same name. All references to `is_checkout()` in LifterLMS have been removed and the original has been left to prevent issues with developers currently relying on the LifterLMS version of thefunction.

= v1.4.5 - 2016/01/13 =
-----------------------

+ Significant improvements to LifterLMS admin permissions as well as a hardening of permissions. Previously LifterLMS admin screens and menus were available to any users with `edit_posts` capabilities. This has been changed to `manage_options`. Filters for all screens and menus have been added with this release. If you're site currently relies on users with `edit_posts` to be able to access LifterLMS settings and analytics screens you must utilize these new filters in order to maintain their access. Please see full documentation on the new filters at [https://lifterlms.readme.io/docs/filters-admin-menu-and-screen-permissions](https://lifterlms.readme.io/docs/filters-admin-menu-and-screen-permissions). **Please consider testing your changes outside of production before updating to LifterLMS 1.4.5 in production.**
+ Allow "Payment Method" to be translated on the "Confirm Payment" screen
+ Allow the name of the payment gateway to be filtered on the "Confirm Payment" screen
+ Added pagination support to lifterlms membership archive pages
+ Fixed a bug related to some required global variables for quizzes and lessons being incorrectly set on certain hosts
+ updated readme file to remove incomplete documentation
+ Added Chosen multi-select options to admin panel metaboxes (settings and posts)
+ Added two new actions that developers can hook into:
	+ `llms_user_enrolled_in_course`, called when users are enrolled in a course. Usage details available [here](https://lifterlms.readme.io/docs/actions-user#llms_user_enrolled_in_course).
	+ `llms_user_added_to_membership_level`, called when users are added to a membership level. Usage details available [here](https://lifterlms.readme.io/docs/actions-user#llms_user_added_to_membership_level).

= v1.4.4 - 2015/12/21 =
-----------------------

##### Updates

+ My account page can now (optionally) display a list of memberships a student is currently enrolled in
+ Student analytics on the admin panel display student's Memberships
+ Student analytics on the admin panel will now display student's progress through courses in addition to their current enrollment status.
+ Custom taxonomy archive templates for Course tags, categories, tracks, and difficulties now exist and properly function.
+ Custom taxonomy archive templates for Membership categories and tags now exist and properly function.
+ Added the `[lifterlms_memberships]` shortcode which was documented but never implemented. Details on usage available at [https://lifterlms.readme.io/docs/short-codes#memberships-lifterlms_memberships](https://lifterlms.readme.io/docs/short-codes#memberships-lifterlms_memberships)
+ Added basic styles to LifterLMS pagination HTML elements (elements with class `.llms-pagination`) which formerly had no associated CSS.

##### Deprecations

+ Setup the `is_shop()` function to be replaced by `is_llms_shop()` function. The original causes conflicts when WooCommerce is installed as WooCommerce includes a core function by the same name. All references to `is_shop()` in LifterLMS have been removed and the original has been left to prevent issues with developers currently relying on the LifterLMS version of thefunction. It *will* be removed in the next major update (2.0) and will be noted as an officially deprecated feature at that time.

##### Bug fixes

+ Fixed pagination issues when using the `[lifterlms_courses]` shortcode
+ Fixed an issue with the `is_shop()` function that prevented courses per page option from functioning properly on the default course archive page
+ Student analytics profile on admin panel will display the correct number of memberships the student is enrolled in.
+ Fixed a small CSS issue that caused extra white space to be displayed above Course or Membership tiles on archive pages when using the WordPress Twentyfifteen default theme

##### Miscellaneus

+ Account settings screen displays the correct title ("Account Settings" it previously said "Archive Settings")
+ Made language changes to the LifterLMS settings intro screen copy
+ Added link to CourseClinic on settings intro screen
+ Added link to LifterLMS documentation on the settings intro screen

= v1.4.3 - 2015/12/11 =
-----------------------

+ Fixed an issue that could prevent some older servers from being able to run LifterLMS

= v1.4.2 - 2015/12/10 =
-----------------------

+ Tested and compatible with WordPress version 4.4
+ BugFixes: fixed issue in `llms_featured_img()` that was preventing the `$size` variable from being passed to the WP core function being utilized.
+ BugFixes: correctly handling conflicts with Plugin Update library

= v1.4.1 - 2015/12/02 =
-----------------------
+ Feature: Custom single price text - Display custom text for the single price on the courses and course page. Custom field does not require a single payment price be set. IE: Free!
+ Feature: Custom Purchase Course Button Text Option. Change the text of the Take This Course button in Settings->Courses.
+ Feature: New Become A Member button on courses that are restricted to memberships.
+ Feature: Custom Become A Member Text Option. Change the text of the become a member button in Settings->Courses.
+ Feature: Paypal Debug Mode. Enable debug mode in Settings->Gateways to view responses from Paypal API when errors occur.
+ Updates: Updated support links in Settings->General.
+ Updates: added minor styling to course page to increase margin and padding for some themes.
+ Updates: Achievement content now available to pull into custom templates. The Achievement content is not by default displayed but can now be used in custom templates.
+ BugFixes: Resolved issue with no default price selected at checkout when only recurring option existed.
+ BugFixes: Lesson prerequisite now alert the user and provide a link to redirect the user to the next required lesson in the course.
+ BugFixes: Paypal errors now return error message instead of white screen when Paypal API fails.
+ BugFixes: Corrected JavaScript error with modals on course edit page in Internet Explorer 11.

= v1.4.0 - 2015/10/29 =
-----------------------
+ Feature: Free lessons - demo lessons that can be taken at any time by any user
+ Feature: Guest lessons - demo lessons that can be taken by a non-logged in user
+ Feature: Random quiz question - quiz questions can now be set to be in user set order or random order
+ Updates: Automatically registers appropriate sidebars for Genesis theme
+ Updates: Backend file cleanup
+ Updates: Text cleanup
+ Updates: Adds greater localization support (more strings to translate! yay!)
+ Updates: Cleans up some unneccessary console.log() calls
+ Updates: Removes mass of commented out code (cleaner reading)
+ Updates: 'Next Lesson' button added after successful completion of quiz
+ Updates: 'Next Lesson' button at bottom of lesson properly gets starting lesson of next section at the end of the previous section
+ Updates: 'Previous Lesson' button at bottom of lesson will now properly get last lesson of previous section (if applicable)
+ Updates: Move Registration Form to global templates to allow users to disable registration on login page but use registration form on custom page.
+ BugFixes: WordPress pages are now properly restricted by memberships
+ BugFixes: Fixes bug that caused order screen to act up if user was deleted
+ BugFixes: Resolves nastly little bug that caused syllabus numbers to be out of whack
+ BugFixes: Resolved error with WooCommerce integration where courses would not always register the user
+ BugFixes: Corrected CSS conflict with Bridge theme settings page

= v1.3.10 - 2015/10/15 =
-----------------------
+ Updates: Clarifies some prerequisite text
+ Updates: Quiz questions are now randomized!
+ Updates: Fixes small CSS issue
+ BugFixes: Resolves fatal errors with a small subset of premium themes

= v1.3.9 - 2015/10/5 =
-----------------------
+ BugFixes: Removes conflict with Yoast SEO
+ BugFixes: Fixes CSS issues with box-sizing takeover
+ Feature: New Settings Tile: Session Management. Found at LifterLMS->Settings->General.
+ Feature: Clear User Session Tool. You can now clear all LifterLMS user session data from your site in LifterLMS->Settings->General
+ Updates: Backend code cleanup

= v1.3.8 - 2015/10/02 =
-----------------------
+ BugFixes: Fixes Random error notices
+ Updates: Updates email template handler

= v1.3.7 - 2015/09/25 =
-----------------------
+ Updates: Adds Spanish translation
+ Updates: Adds new filter 'lifterlms_single_payment_text' to customize single payment string on checkout
+ Updates: Student analytics now indicate which courses a student has completed
+ BugFixes: Resolved security issue with WordPress searches and lessons
+ BugFixes: Fixes analytics bug that potentially arises after a course is deleted

= v1.3.6 - 2015/09/18 =
-----------------------
+ BugFixes: Fixes pesky Zend Error that plagued some unfortunate victims
+ BugFixes: Students can now be properly deleted from the course
+ BugFixes: Fixes random class redeclaration error messages
+ Updates: Adds new filter 'lifterlms_quiz_passed' to customize 'Passed' text after quiz
+ Updates: Adds new filter 'lifterlms_quiz_failed' to customize 'Failed' text after quiz

= v1.3.5 - 2015/09/11 =
-----------------------
+ Revisions: Fixes typos
+ Updates: Adds sidebar functionality to various themes

= v1.3.4 - 2015/09/04 =
-----------------------
+ BugFixes: Fixes bug with featured image on course page
+ BugFixes: Fixes issue with lesson completed percentage on analytics page

= v1.3.3 - 2015/09/01 =
-----------------------
+ Updates: Removes depricated plugin updater
+ Updates: Adds Course Track prerequisite
+ Updates: Various text fixes
+ BugFixes: Fixes lesson name on prerequisite notification
+ BugFixes: Fixes critical error with WordPress customizer

= v1.3.2 - 2015/08/30 =
-----------------------
+ Hotfix: resolves issues with sidebar shortcodes
+ Updates: Text clarifications

= v1.3.1 - 2015/08/28 =
-----------------------
+ Hotfix: resolves issue with ajax url

= v1.3.0 - 2015/08/28 =
-----------------------
+ Improved popopver behavior in course creation.
+ BugFixnig. Prevent multiple lesson and section form submition
+ Fixed typos at backend quiz page
+ Fixed check for update bug when plugin isn't properly activated.
+ BugFixing, quiz post type should show author metabox
+ Added course category filter to lifter_lms shortcode
+ BugFixing, typo in [lifterlms_course_progess shortcode]
+ BugFixing, Analytics shouldn't fetch students meta info from users were deleted.
+ Adds in basic review functionality
+ Updates plugin-updater to remedy PHP conflicts
+ Fixes date bug in Analytics
+ Cleans up jQuery console messages
+ Adds in course tracks

= v1.2.8 - 2015-07-17 =
-----------------------
+ Updated Portuguese translation file
+ Fixed issue where quiz score could not be equal to required grade.
+ New Feature: Quiz Results Summary. Display the quiz results to the user on quiz completion.
+ New feature: Clarification. Display information about correct and incorrect answers to users
+ New Feature: Display correct answers to user on quiz completion
+ Removed ability to add negative time limit to quiz
+ New Membership feature: Make membership archive links go directly to checkout. Setting allows you to skip membership sales page and send users directly to registration and checkout.
+ Sidebar support for prototype theme
+ Sidebar support for X theme
+ Sidebar support for WooCanvas
+ New Shortcode: [lifterlms_hide_content]: Use to restrict content on a page, course or lesson to a specific membership. Pass the post id of the membership you want to restrict the content to. Example: [lifterlms_hide_content membership="5"]
+ New updates to gulp build process
+ Class autoloading and LLMS namespace introduced for more efficient coding.

= v1.2.7 - 2015-06-05 =
-----------------------
+ Minor bug fix with lesson redirect to quiz
+ Minor change to global Course object instantiation.
+ Bug Fix: Remove student from course
+ Bug Fix: Appearance Menus missing select field (THANKS ANDREA!)
+ New Course Setting: Hide Course Outline on course page
+ New Shortcode: [lifterlms_course_outline] - displays course outline with settings (see documentation)
+ Membership metabox design update
+ Certificate metabox design update
+ Achievement metabox design update
+ Lesson metabox design update
+ Emails metabox design update
+ Coupons metabox design update
+ Update to certificate design (better alignment and theme functionality)
+ Better theme sidebar support
+ More awesome control for devlopers building new settings for LifterLMS
+ Advanced filter system for metabox fields with finite control for 3rd party developers.
+ Woocommerce confict correction to archive templates
+ Style updates to allow themes better control on design

= v1.2.6 - 2015-04-28 =
-----------------------
+ Corrected issue with lesson re-order on save
+ corrected html formatting issue on purchase page
+ corrected html formatting issue on course page

= v1.2.5 - 2015-04-23 =
-----------------------
+ Corrected excerpt to not pull in lesson navigation
+ Modified metabox api for better extension integration
+ Corrected issue with order not displaying all information if coupon was not applied to order

= v1.2.4 - 2015-04-22 =
-----------------------
+ Moved All Course metaboxes to global Course Options Metabox
+ Move Enrolled and Non-Enrolled user wysiwyg post editors to Options Metabox
+ Removed Course Syllabus metabox, Added Course Outline Metabox
+ Set priority of Course Outline and Course Options Metabox to top
+ Added ability to Create new section to Course Outline
+ Added abiliyt to Create new lesson to Course Outline
+ Added ability to add existing Lesson to Course Outline
+ Added Lesson duplicate functionality when adding lesson previously assigned to another course.
+ Added ability to drag lessons between sections in Course Outline
+ Added ability to edit Section Title in Course Outline
+ Added ability to edit lesson title and excerpt in Course Outline
+ Added New Style and Design for better usability to Course Outline
+ Added Lesson Icon with tooltip to Course Outline: Prerequisite - shows if prerequisite exists and displays name of prerequisite
+ Added Lesson Icon with tooltip to Course Outline: Quiz - shows if quiz is assigned to course and displays name of quiz
+ Added Lesson Icon with tooltip to Course Outline: Drip Content - shows if drip days are set and # of days
+ Added Lesson Icon with tooltip to Course Outline: Content - displays if lesson has content added.
+ Added Course Outline Metabox to Lesson Post Editor: Allows you to assign lesson to section and view entire course tree. Links to Course and all other lessons in course.
+ Style Update: backgrounds on frontend. Removed all references to white background on front end elements
+ Corrected Restriction for course in past. Updated course in past message to display as Course ended instead of Course not available until.
+ Added restriction message when user attempts to visit a restricted lesson.
+ Updated course syllabus sidebar widget to not display lessons as links if user is not enrolled in course.
+ Added ability to use Attribute Order for sorting Courses and Memberships on Archive pages.
+ Added support for selling memberships with Woocommerce. LifterLMS now checks memberships for SKU matches in addition to Courses when products are purchased using WooCommerce.
+ Added gulp for scss, js and svg management
+ Added svg sprite and svg class for managing svg elements on front and backend.
+ Added better language translation support for strings
+ Refactored Ajax Classes for cleaner, faster development
+ Refactored metabox build class for cleaner, faster development
+ Refactored Course syllabus to reduce query size for larger, complex courses
+ Added Handler classes for Lessons, Sections, Courses and Posts
+ Refactored Course get / set methods to reduce database queries

= v1.2.3 - 2015-03-12 =
-----------------------
+ Achievement design and functionality updates
+ Achievemnt shortcode added
+ Better searching added to engagement screen
+ Achievement bug fixes
+ On screen error reporting added to activation for trouble shooting
+ Custom engagement methods added to certificate, achievement and sections
+ Corrected new user registration engagement bug
+ LifterLMS access reduced from manage_options to edit_posts
+ Filters added to analytics to allow custom developement
+ Engagment bug fix: Section and Lesson bug select
+ Syllabus bug corrected: No longer displays lessons in section box if no sections exist.
+ Removed depreciated achievement template
+ Membership Bug fix: Membership restriction will now only display on single posts.


= v1.2.2 - 2015-02-23 =
-----------------------
+ Corrected drip content bug
+ Added Ajax functionality to quiz
+ rounded quiz grades
+ Added quiz time limit setting to Quiz
+ Added quiz timer to quiz, front end
+ Quiz allowed attempts field now allows unlimited attempts
+ Set Ajax lesson delete method to not return empty lesson value
+ Set next and previous questions to display below quiz question
+ Decoupled Single option select question type from quiz to allow for more question types
+ Added Quiz time limit to display on Quiz page
+ Added functionality to automatically complete quiz when quiz timer reaches 0
+ Moved Quiz functionality methods from front end forms class to Quiz class

= v1.2.1 - 2015-02-19 =
-----------------------
+ Updated settings page theming
+ Added Set up Quick Start Guide
+ Added Plugin Deactivation Option
+ Updated language POT file
+ Added Portuguese language support. Thank you Fernando Cassino for the translation :)


= v1.2.0 - 2015-02-17 =
-----------------------
+ Admin Course Analytics Dashboard Page. View at LifterLMS->Analytics->Course
+ Admin Sales Analytics Dashboard Page. View at LifterLMS->Analytics->Sales
+ Admin Memberships Analytics Dashboard Page. View at LifterLMS->Analytics->Memberships
+ Admin Students Search Page. View at LifterLMS->Students
+ Admin Student Profile Page ( View user information related to courses and memberships )
+ Lesson and Course Sidebar Widgets ( Syllabus, Course Progress )
+ Course Syllabus: Lesson blocks greyed out. Clicking lesson displays message to take course.
+ Misc. Front end bug fixes
+ Misc. Admin bug fixes
+ Course and Lesson prerequisites: Can no longer select a prerequisite without marking "Has Prerequisite"
+ Admin CSS updates
+ Better Session Management
+ Number and Date formatting handled by seperate classes to provide consistant date formats across system
+ Zero dollar coupon management: Coupons that set total to 0 will bypass payment gateway, generate order and enroll users.
+ Better coupon verification.
+ Better third party payment gateway support. Third party gateway plugins are now easier to develop and integrate.
+ User Registration: Phone Number Registration field option now available in Accounts settings page.

= v1.1.2 - 2014-12-18 =
-----------------------
+ Moved Sidebar registration from plugin install to init

= v1.1.1 - 2014-12-16 =
-----------------------
+ Added user registration settings to require users to agree to Terms and Conditions on user registration
+ Added comments to all classes methods and functions
+ Removed unused and depreciated methods
+ Added Lesson and Course Sidebar Widget Areas
+ Fixed bug with course capacity option
+ Fixed bug with endpoint rewrite
+ Added localization POT file and us_EN.po translation file

= v1.1.0 - 2014-12-08 =
-----------------------
+ Updated HTML / CSS on Registration form
+ Added Coupon Creation
+ Added Coupon support for checkout processing
+ Added Credit Card Support processing support
+ Added Form filters for external integration
+ Added Form templates for external integration
+ Added Account Setting: Require First and Last Name on registration
+ Added Account Setting: Require Billing Address on registration
+ Added Account Setting: Require users to validate email address (double entry)
+ Added password validation (double entry) on user registration / account creation
+ Added Quiz Question post type and associated metaboxes
+ Added Quiz post type and associated metaboxes
+ Added ability to assign a quiz to a lesson
+ Added front end quiz functionality
+ Added Course capacity (limit # of students)

### User Admin Table
+ Added Membership Custom Column that displays user's membership information
+ Added "Last Login" custom column that displays user's last login date/time

### User Roles
+ Updated user role from "person" to "student"
+ Added temporary migration function to transition any register users with "person" role to "student" role
+ Added "Student" role install function


### BUDDYPRESS
+ BuddyPress Screen Permission Fix
+ Added two additional screens to BuddyPress: Certificates and Achievements

### MISC
+ Added llms options for course archive pagination and added course archive page pagination template
+ Added user statisticc shortcode


= v1.0.5 - 2014-11-12 =
-----------------------

+ Fixed a mis-placed parenthesis in templates/course/lesson-navigation.php related to outputting excerpt in navigation option
+ Changed theme override template directory from /llms to /lifterlms
+ Update the positiong & name of the "My Courses" Menu in BuddyPress Compatibility file
+ New meta_key _parent_section added for easier connection and quicker queries.
+ Section sorting on course syllabus
+ Edit links added to course syllabus
+ Assign section to course and view associated lessons metabox added to sections
+ Assign lesson to section and view associated lessons metabox added to lessons
+ Assigned Course, Assigned Section, Prerequisite and Membership Required added to lesson edit grid
+ Assigned Course added to section edit grid'
+ New membership setting: Restrict Entire Site by Membership Level (allows site restriction to everything but membership purchase and account).
+ Updated template overriding to check child & parent themes
+ Updated template overriding to apply filters to directories to check for overrides to allow themes and plugins to add their own directories

= v1.0.4 - 2014-11-04 =
-----------------------

+ Templating bug fix
+ Added shortcode and autop support to course and lesson content / excerpt


= v1.0.3 - 2014-11-04 =
-----------------------

+ Major Templating Update!
+ Removed Course, Lesson and Membership single lesson templates.
+ Course and Section content templates now filter through WP content


= v1.0.2 - 2014-10-31 =
-------------------------

+ Added lesson short description to previous lesson preview links -- it was rendering on "Next" but not "Previous"
+ Added a class to course shop links wrapper to signify the course has been completed
+ Removed an uncessary CSS rule related to the progress bar


= v1.0.2 - 2014-10-30 =
-----------------------

+ Fixed SSL certificate issues when retreiving data from https://lifterlms.com
+ Added rocket settings icon back into repo


= v1.0.1 - 2014-10-30 =
-----------------------

+ Updated activation endpoint url to point towards live server rather than dev