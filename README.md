# Build Custom Blocks In Gutenberg With ACF

## 1. Install the Plugin

In order to use this functionality, you need the Pro version of ACF 5.8 or higher. You can purchase it on the <a href="https://www.advancedcustomfields.com/pro/" target="_blank">main website.</a>

Once on your hard drive, log into your site and go to Plugins > Add New > Upload Plugin.

Hit Browse…, find the file on your computer, and click Install Now. Once done, don’t forget to activate it.

## 2. Register Your Block

Here’s an explanation of what it all means:

Step 1 https://snipboard.io/ETudL1.jpg
Step 2 https://snipboard.io/589maK.jpg
Step 3 https://snipboard.io/zU7fmt.jpg
Step 4 https://snipboard.io/zU7fmt.jpg

## Upload block files 

Create this type folder structure
/wp-content/themes/child-theme/blocks/tabs
https://snipboard.io/rXRDK3.jpg


## Create Your Fields

After including the above code in functions.php, you will already be able to see your block in the Gutenberg editor.


## Add below code with function.php file

///////////////////////////////// Fucntion.php file code ////////////////////////

add_action('acf/init', 'my_acf_init');
function my_acf_init() {
    
    // check function exists
    if( function_exists('acf_register_block') ) {
        
        // register a tabs block
        acf_register_block(array(
            'name'              => 'Tabs',
            'title'             => 'Tabs',
            'description'       => 'A custom tabs block.',
            'render_callback'   => 'my_acf_block_render_callback',
            'category'          => 'formatting',
            'icon'              => 'admin-comments',
            'keywords'          => array( 'tabs', 'quote' ),
        ));
    }
}

function my_acf_block_render_callback( $block ) {  
  
  if( file_exists( get_theme_file_path("/blocks/tabs/content-tabs.php") ) ) {
      include( get_theme_file_path("/blocks/tabs/content-tabs.php") );
  }


## After that you can see the block backend.

Backend - https://snipboard.io/c9weBj.jpg (Add some content here.)


## You can se frontend.

Frontend - https://snipboard.io/W2cD5L.jpg

