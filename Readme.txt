=== Transparent Secured Images ===
Contributors: michederoide
Tags: secured, images, pictures, transparent, watermark
Requires at least: 3.0
Tested up to: 3.3
Stable tag: 1.0

Secure your images with a transparent picture (CSS3 compatible browser required!)

== Description ==

This plugin will use jQuery and JavaScript, as well as CSS3, to secure your images a little bit more.

NOTE: It is NOT possible to completely secure your images since all browsers have to get them in order to show them your users, but we do a little approach to secured pictures.

The plugin will replace your image with a transparent image and set your image, you want to show to the user, as background image of the container. When the user now tries to copy the url of the image or the picture itself, he will only get the transparent png file.

== Installation ==

1. Upload all files to a directory of your choice (it has to be available through your domain)

2. Copy the following code into your theme header before "</head>" (use the editor of Wordpress for this)

<script type='text/javascript' src='https://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js'></script>
<script type='text/javascript' src='[ADDON.JS]'></script>
<script type='text/javascript'>
$(document).ready(function () {
  if($.support.cssProperty('backgroundSize'))
  {
    $('#content img').each(function() {
      var temp = $(this);
      var width = temp.width();
      var height = temp.height();
      var src = temp.attr('src');
      var id = temp.attr('alt').replace(/\s/g, '');
      temp.wrap('<div id="#' + id + '" />');
      $(this).parent().css('backgroundImage', 'url("' + src + '")');
      $(this).parent().css('backgroundSize', '100%');
      temp.attr('src', '[TRANSPARENCY.PNG]');
      $('div#' + id + ' img').replaceWith(temp);
    });
  }
});
</script>

3. Replace "[TRANSPARENCY.PNG]" in the above code with the url to the transparency.png file

4. Replace "[ADDON.JS]" in the above code with the url to your addon.js file

5. Enjoy your secured pictures

== Frequently Asked Questions ==

We do currently have no FAQ!

== Changelog ==

= 1.0 =
* Initial release
* Currently we need jQuery to load from google (we search for another option yet)