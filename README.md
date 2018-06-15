# WP-Bulma-Navwalker
A WordPress Bulma CSS Framework NavWalker with Font Awesome Support.

## Install
Drop the file into your WordPress theme folder and hook up to it in your functions.php

```php
require_once('classes/bulma-navwalker.php');
```

Setup the Bulma NavBar and wp_nav_menu in header.php.  This demo example uses is-fixed-top and navbar-end from the bulma CSS Framework.  Please consult the documentation for other options https://bulma.io/documentation/components/navbar/
```
	<nav class="navbar is-fixed-top" aria-label="main navigation">
		<div class="navbar-brand">
			<a class="navbar-item" href="<?php echo esc_url( home_url( '/' ) );?>">
					<img alt="My Logo" src="<?php echo get_template_directory_uri();?>/images/my-logo.png">
			</a>

		 <button class="button navbar-burger is-active" data-target="primary-menu" aria-controls="primary-menu" aria-haspopup="true" aria-label="Menu Button" aria-pressed="false">
			 <span aria-hidden="true"></span>
			 <span aria-hidden="true"></span>
			 <span aria-hidden="true"></span>
		 </button>
 </div>

 <div id="primary-menu" class="navbar-menu is-active">
	 <div class="navbar-end">
		 <?php wp_nav_menu(array(
			 'theme-location' => 'header-menu', //change it according to your register_nav_menus() function
			 'depth'		=>	3,
			 'menu'			=>	'NewNav',
			 'container'		=>	'',
			 'menu_class'		=>	'',
			 'items_wrap'		=>	'%3$s',
			 'walker'		=>	new Bulma_NavWalker(),
			 'fallback_cb'	=>	'Bulma_NavWalker::fallback'
		 ));
		 ?>
	 </div>
</div>
</nav>
```
##Configuration
Enqueue Font Awesome in functions.php

```php
function wow_scripts() {
//include other scripts and styles too
	wp_enqueue_script('font-awesome','//use.fontawesome.com/releases/v5.0.13/js/all.js',null,null,true);
}

add_action( 'wp_enqueue_scripts', 'wow_scripts' );
```  

###Displaying Font Awesome 5 Icons (Not tested on earlier versions but should work)
Tested on top level navigation links!
Find the icon code snippet from https://fontawesome.com/icons?d=gallery
Add the snippet into the **css class** box located in **Appearance->Menus**

Example:
```
fas fa-info-circle
```

###Displaying The title Alongside The Icon
Add the class **fa-show-title** to the **css class** box
Leave it blank if you only want to display the icon

###NavBar Divider
Tested on dropdowns
Add a custom link using # in the url box
Add the class **navbar-divider** to the **css class** box

###Alignment Class
The class **is-right** can be used on the farthest dropdown when using the navbar-end class.  It simply aligns the dropdown so that is doesn't overflow the page. Simply add **is-right** to the parent element.

##Future Features and Bugfixes
Although I have thoroughly tested the NavWalker if you come across any errors or bugs please report any issues.

####Possible Future Features
Integrate Bulma Mega-Menu
Search Bar
Social Icons etc
