# Setting-Cookies-with-jQuery
Create a cookie that will expire in 365 days or 24 hours

This a demo of setting cookies with jQuery.

#### The three settings are:

- create a cookie that will expire in 365 days but it will then open a sample survey inside of jQuery UI modal.
- create a cookie that will expire in 24 hours but will NOT open a sample survey inside of jQuery UI modal but as the cookies is set for 24 hours, will ask again.
- create a cookie that will expire in 365 days but it will NOT open the sample survey.

#### CSS Dependencies:
- jquery.fancybox.css
- jquery.ui.all.css

#### jQuery cookie Dependencies:    
- jquery.js
- jquery.fancybox.js
- jquery.cookie.js

#### jQuery UI Dependencies: 
- jquery.ui.core.js
- jquery.ui.widget.js
- jquery.ui.position.js
- jquery.ui.button.js
- jquery.ui.dialog.js
- jquery.ui.effect.js
- jquery.ui.effect-fade.js

#### The jQuery:
```js
// Set the cookie so if the user selects either YES, I would like to participate or, 
// If the user selects NO Thanks, Don't ask me again, we create a cookie that will expire in 365 days.
// That will ensure the fancy box does not display again unless the user clears their browser cookies.
	
    // call fancybox
    function openFancy(){ 
   		setTimeout( function() {$('#autoStart').trigger('click'); }, 1000); // [200000] = show after 20 seconds
    } 
	
    // create cookie on button click
    function dontShow(){
		$.fancybox.close(); // optional
		$.cookie('visited', 'yes', { expires: 365 }); // expiration in 365 days
    }
	
    $(document).ready(function() {
		var visited = $.cookie('visited'); // create cookie 'visited' with no value
		if (visited == 'yes') {
		return false;
    } 
	
	else {
    	openFancy(); // cookie has no value so launch fancybox on page load
    }
		
   		$('#autoStart').fancybox(); // anchor tag with an id so it triggers the dialog modal on page load
		
    });

	// Set the cookie so the user will see the fancy box the next time the user visits the site.
	// The cookie is set to expire in 24 hours. This will ensure the fancy box will display again after 24 hours.
	
    // call fancybox
    function openFancy(){ 
   		setTimeout( function() {$('#autoStart').trigger('click'); }, 1000); // [200000] = show after 20 seconds
    } 
	
    // create cookie on button click
    function maybeLater(){
		$.fancybox.close(); // optional
		$.cookie('visited', 'yes', { expires: 1 }); // expiration in 1 day
    }
	
    $(document).ready(function() {
		var visited = $.cookie('visited'); // create cookie 'visited' with no value
		if (visited == 'yes') {
		return false;
    } 
	
	else {
    	openFancy(); // cookie has no value so launch fancybox on page load
    }
	
   		$('#autoStart').fancybox();
		
    });
	
	$(function() {
		$( "#dialog" ).dialog({
			autoOpen: false,
			height: 600,
			 width: 600,
			 modal: true,
			 buttons: {
					Submit: function() {
					$( this ).dialog( "close" );
					}
			 },
			 
			show: {
				effect: "fade",
				duration: 1000
			},
			hide: {
				effect: "fade",
				duration: 1000
			}
		});

		$( "#opener" ).click(function() {
			$( "#dialog" ).dialog( "open" );
		});
	});
