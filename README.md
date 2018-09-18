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
main, 991px, 767px must include the same class name to do style at different width.
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
	1. checkout dev, update, 
	2. right click on tab
	3. Git, compare with Branch, choose local branch, and manully merge

# CSS 
	use min-width to avoid the line jump to second page when shrinks the screen size
	
# UTM Builder Javascript
	<script>
        function writeUtm(utm, name, html) {
            if (utm) {
                if (html[1] == 0) {
                    html[0] += '?';
                }
                else {
                    html[0] += '&';
                }
                html[0] += name + '=' + encodeURIComponent(utm);
                html[1]++;
            }
            return html;
        }

        function updateOutput() {
            var domain = $('#domain').val();
            var utm_source = $('#source').val();
            var utm_medium = $('#medium').val();
            var utm_term = $('#term').val();
            var utm_content = $('#content').val();
            var utm_campaign = $('#name').val();
            var utm_campaign_input = $('#name_input').val();

            var html = [];
            html[0] = domain;
            html[1] = 0;

            html = writeUtm(utm_source, 'utm_source', html);
            html = writeUtm(utm_medium, 'utm_medium', html);
            html = writeUtm(utm_term, 'utm_term', html);
            html = writeUtm(utm_content, 'utm_content', html);
            if (!utm_campaign_input) {
                html = writeUtm(utm_campaign, 'utm_campaign', html);
            } else {
                html = writeUtm(utm_campaign_input, 'utm_campaign', html);

            }


            if (domain) {
                $('#url').html(html[0].replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;"));
            } else {
                $('#url').html('');
            }


        }

        $(function () {
            $("form").bind("click keyup change", function (e) {
                updateOutput();
            });
        });

        function copyUrl() {
            var copyText = document.getElementById("url");
            copyText.select();
            document.execCommand("copy");
            // alert("Copied the text: " + copyText.value);
        }

    </script>
	
# CSS correct target:
	use dev tool to hover the class,
	div.class name.class name use space next level.class name
	
# duplicated meta descriptions and titles
	at seo -> add %%page%% at description and title will solve this problem
	
# uncaught TypeError: $(...).tooltip is not a funciton Issue:
	to solve this problem, first to find correct header.php file.
	for example, at header-sr.php, $sr2page == 'concretematuritytool'
	second, add <script src="https://code.jquery.com/ui/../jquery-ui.js"> just behind jquery.js
	
	or just delete the jquery.js(it may be called twice) 
	
# useful tools to check website:
	1.semrush
	2.Search Console
	3.gtmetrix
	4.Google Analytics

# 301 re-direct:
	/.../* => /.../.../*

# export live database to local
	live phpmyAdmin -> export
	local phpmyAdmin -> import

# SCSS and LESS syntax:
	&.class-name {} => parallel with last class
	
# wp responsive image function:
	function awesome_acf_responsive_image($image_id,$image_size,$max_width){

	// check the image ID is not blank
	if($image_id != '') {

		// set the default src image size
		$image_src = wp_get_attachment_image_url( $image_id, $image_size );

		// set the srcset with various image sizes
		$image_srcset = wp_get_attachment_image_srcset( $image_id, $image_size );

		// generate the markup for the responsive image
		echo 'src="'.$image_src.'" srcset="'.$image_srcset.'" sizes="(max-width: '.$max_width.') 100vw, '.$max_width.'"';

	}
}
  and to call function in <img <?= awesome_acf_responsive_image($conten['image'][0]['id'],'thumb-640','640px'); ?>

# wp get image alt description from the uploads
	use <?php $image_alt=get_post_meta(get_post_thumbnail_id( $post->ID ), '_wp_attachment_image_alt', true) ?> to retrieve the alt information, then use alt="<?php echo !empty($image_alt) ? $image_alt : 'Construction of Concrete Wall with Formwork'?>" to display alt description
	
# wp add custom field
	1. go to Custom Fields
	2. go to specific field groups
	3. add new field give field label
	4. field type should be tab
	5. add new field give field label and field name
	6. field type can be anything
	7. use wp function to call the data from field by using field_name
	for example: 	$post_id = get_the_ID();
			$company_logo = get_field('company_logo', $post_id);
# wp add seo to a page
	seo->search appearance->content types->choose the page need to be seo 

# wp background-image set to be responsive, call different size when in different screen size
	<?php
        $imageFull = wp_get_attachment_image_src(get_post_thumbnail_id($post_id), 'full');
        $imageLarge = wp_get_attachment_image_src(get_post_thumbnail_id($post_id), 'large');
        $imageMediumLarge = wp_get_attachment_image_src(get_post_thumbnail_id($post_id), 'medium_large');

        $imageFull = !empty($imageFull[0]) ? $imageFull[0] : '/wp-content/uploads/2018/09/boot.jpg';
        $imageLarge = !empty($imagelarge[0]) ? $imagelarge[0] : $imageFull;
        $imageMediumLarge = !empty($imageMediumLarge[0]) ? $imageMediumLarge[0] : $imageLarge;
        ?>
    <?php } else
    {
        $imageFull = !empty($imageFull) ? $imageFull : '/wp-content/uploads/2018/09/boot.jpg';
        $imageLarge = !empty($imageLarge) ? $imageLarge : '/wp-content/uploads/2018/09/boot-1024x576.jpg';
        $imageMediumLarge = !empty($imageMediumLarge) ? $imageMediumLarge : '/wp-content/uploads/2018/09/boot-768x432.jpg';
    }
    ?>
    <style>
        .header {
            background-image: url(<?=$imageFull?>);
        }

        @media (max-width: 991px) {
            .header {
                background-image: url(<?=$imageLarge?>);
            }
        }

        @media (max-width: 767px) {
            .header {
                background-image: url(<?=$imageMediumLarge?>);
            }
        }
    </style>
    
 # Url Shortener
 	https://github.com/jmccartie/php-url-shortener
	1.downlkoad code from github
	2.do configuration on config.php
	3.modify connect.php, create.php, index.php, view.php
	4.if sql doesn't support, change sql into sqli
	5.upload all files to server(must include .htaccess file)
	6.type in url: A.Get Method: domin/create.php?url=...&pw=...
		       B.Post Method: 

# FTP Configuration
	1. set up ftp account in the server (Make sure the Directory is correct and identical the the phpstorm)
	2. in phpstorm, tools -> deployment -> configuration -> + add new one -> choose typy to FTP -> FTP host (should be 	      server host) -> Root path(/ or try auto detect) -> user name and password (identical to server FTP account) ->              deployment path on server(/)
	3. options: ctrl + s, automatic uploads
	
# PHP add password to page
	check view.php at giatec.net
	
# js LinkedIn page crawler
	function JSONToCSVConvertor(JSONData, ReportTitle, ShowLabel) {
    //If JSONData is not an object then JSON.parse will parse the JSON string in an Object
    var arrData = typeof JSONData != 'object' ? JSON.parse(JSONData) : JSONData;

    var CSV = '';
    //Set Report title in first row or line


    //1st loop is to extract each row
    for (var i = 0; i < arrData.length; i++) {
        var row = "";

        //2nd loop will extract each column and convert it in string comma-seprated
        for (var index in arrData[i]) {
            row += '"' + arrData[i][index] + '",';
        }

        row.slice(0, row.length - 1);

        //add a line break after each row
        CSV += row + '\r\n';
    }

    if (CSV == '') {
        alert("Invalid data");
        return;
    }

    //Generate a file name
    var fileName = "Giatec_";
    var today = new Date();
    var date = '_' + today.getFullYear()+'_'+(today.getMonth()+1)+'_'+today.getDate()+'_';

    //this will remove the blank-spaces from the title and replace it with an underscore
    fileName += ReportTitle.replace(/ /g, "_");

    //Initialize file format you want csv or xls
    var uri = 'data:text/csv;charset=utf-8,' + escape(CSV);

    // Now the little tricky part.
    // you can use either>> window.open(uri);
    // but this will not work in some browsers
    // or you will not get the correct file extension

    //this trick will generate a temp <a /> tag
    var link = document.createElement("a");
    link.href = uri;

    //set the visibility hidden so it will not effect on your web-layout
    link.style = "visibility:hidden";
    link.download = fileName + date +".csv";

    //this part will append the anchor tag and remove it after automatic click
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);
}

jQuery(function ($) {
    var data = [], list = [];
    var rand = Math.round(Math.random() * (3000)) + 3000;
    var rand2 = Math.round(Math.random() * (3000)) + 2000;
    list['first_name'] = 'First Name';
    list['last_name'] = 'Last Name';
    list['job_title'] = 'Job Title';
    list['company'] = 'Company';
    list['location'] = 'Location';
    list['domain'] = 'Domain';
    list['contact_name'] = 'Contact Name';
    list['campaign'] = 'Campaign';
    list['rating'] = 'Rating';
    list['country'] = 'Country';
    list['state'] = 'State';
    data.push(list);
    var interval = window.setInterval(function () {
        rand = Math.round(Math.random() * (8000 - 5000)) + 3000;
        rand2 = Math.round(Math.random() * (8000 - 5000)) + 2000;
        $("html").animate({scrollTop: $(document).height() * 2}, rand2, function () {
            jQuery('.search-results__result-item').each(function (index, element) {
                list = [];
                var name = $(element).find("dt.result-lockup__name a.ember-view");
                list['first_name'] = $(name).text().split(' ')[12].trim();
                list['last_name'] = $(name).text().split(' ')[13].trim();
                var job_title = $(element).find('dd.result-lockup__highlight-keyword > span:first-child');
                list['job_title'] = $(job_title).text().trim();
                var company_name = $(element).find('.horizontal-person-entity-lockup-4.result-lockup__entity.ml4 dd.result-lockup__highlight-keyword .result-lockup__position-company a > span:first-child');
                list['company'] = $(company_name).text().trim();
                var location_name = $(element).find('ul.result-lockup__misc-list li.result-lockup__misc-item');
                list['location'] = $(location_name).text().trim();
                list['domain'] = '';
                list['contact_name'] = '';
                list['campaign'] = '';
                list['rating'] = '';
                list['country'] = '';
                list['state'] = '';
                data.push(list);
            });
            if (!jQuery('button.search-results__pagination-next-button').is(':disabled')) {
                jQuery('button.search-results__pagination-next-button').trigger('click');
            } else {
                clearInterval(interval);
                JSONToCSVConvertor(data, $('.search-nav--title a').text(), false);
            }
        });
    }, rand + rand2);
});

# Imac signature issue
https://www.daretothink.co.uk/html-email-signature-in-apple-mail/
