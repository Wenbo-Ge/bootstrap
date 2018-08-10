# CSS stuff
install sass to edit .scss files 
# CSS Selector
div > p : select all p where parent is a div
# Css Position
  position: static will put div next to the element in another div
# CSS and JS Cache Issue
  .css/.js?v=1:1, add <?= rand() ?> to the stylesheet link<> to clear the cache
# CSS Responsive
@media (min-width:991) {
  .mobile_display {
    display:none
  }
}
screen size larger than 991px will display none
# CSS responsive image
php hard code, use http://www.responsivebreakpoints.com/ to generate responsive image
<img
								sizes="(max-width: 728px) 100vw, 728px"
								srcset="
<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_200.jpg 200w,
<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_392.jpg 392w,
<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_542.jpg 542w,
<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_661.jpg 661w,
<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_728.jpg 728w"
								src="<?php echo get_template_directory_uri(); ?>/templates-giatec/images/product_smartrock_sz08nl_c_scale,w_728.jpg"
								alt="SmartRock2&trade;">

# JS
to keep same height of each div, write js to calculate the height and use the largest height.

# JS 遍历+查找
<script>

   jQuery(document).ready(function(){


        jQuery('.bg_image').each(function(){
            var highestBox = 0;
            jQuery(this).find('.post .post_content').each(function () {
                    if (jQuery(this).height() > highestBox) {
                        highestBox = jQuery(this).height();
                    }
                }).height(highestBox);
        });
});

</script>
# JS responsive change height and resize
+<script>
+
+function call(){
+    var w = jQuery(window).width();
+    if(w > 767) {
+
+        jQuery('.bg_image').each(function(){
+
+            // Cache the highest
+
+            var highestBox = 0;
+
+            // Select and loop the elements you want to equalise
+            jQuery(this).find('.post_content').each(function(){
+                jQuery(this).removeAttr('style');
+                // If this box is higher than the cached highest then store it
+                if(jQuery(this).height() > highestBox) {
+                    highestBox = jQuery(this).height();
+                }
+
+            }).height(highestBox);
+        });
+
+        // Select and loop the container element of the elements you want to equalise
+
+
+
+    }else{
+        jQuery('.bg_image .post_content').removeAttr('style');
+
+    }
+}
+            jQuery(document).ready(function(){
+                call();
+
+                jQuery(window).resize(function() {
+                   call();
+            });
+            });
+
+
+</script>
+
# CSS stylesheet in Wordpress
wordpress: <?php echo get_css_directory(); ?>
example:
<link rel="stylesheet" href="<?php echo get_css_directory(); ?>/sr2/animate.css?v=july272018348pm"/>

# CSS Selector
<li ><a href="<?php echo site_url(); ?>/blog"><span class="breadcrumb-item active" aria-current="page">Blog</span></a></li>
span.breadcrumb-item.active {
           color: #368e47;
       }
       
# CSS extend img to full width in a div
    width: 100vw;
    position: relative;
    left: 50%;
    margin-left: -50vw;
    right: 50%;
    margin-right: -50vw;
    
# PHP
put in the header.php
 <?php
    $postType = "company-news";
    switch ($postType) {
        case "company-news":
            $meta = 'Keep up with all Giatec updates and exciting company news. These articles give you all the latest updates including trade shows, awards, contests, and more. Giatec was recently presented with Ottawa’s Fastest Growing Companies Award';
            break;
        case "press":
            $meta = '';
            break;
        case "video":
            $meta = '';
            break;
    }
    ?>
    <meta name="description" content="<?php echo $meta ?>"/>

# GIT of BitBucket
	1. check terminal: should be under giatec@mail:
	2.git process:
	  1.create new branch at PHP storm, checkout dev, update, create new branch.
	  2.edit files and push at php storm
	  3.go to bb copy the link to fetch and checkout at terminal
	  4.git branch to check branch
	  5.ever push at php storm, pull at terminal. if wrong, git reset --h. then git pull
	  
	3. create pull resquest, got to bb, branch to dev
# Merge
	1. checkout dev, update, merge branch into current,
	2. regenerate scss, push.
	3. terminal checkout dev and git pull
