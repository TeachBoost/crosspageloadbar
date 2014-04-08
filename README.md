Cross page loading bar for JQuery
==========================================

A small javascript library that displays a small loading bar when a website is navigating through
various pages.

When a page unloads, a tiny loading bar is displayed on the top of the browser window and resumes
from the previous state when the new page loads, giving the perception of a seamless navigation.

This is useful for websites with pages that might take some time to load.

Works automatically with pjax and jquery ajax calls as well.

Cross site loading on Safari is disabled as the Safari address bar already
emulates the purpose of this library.

When you have a link that downloads a file, the window.onbeforeunload event is fired, which
may lead to an improper appearance of the loading bar. To avoid this just enable the
"enable_filedownload" settings, and set a selector for your links using the
"filedownload_anchor_selector" setting, e.g.

```html
...
window.CrossPageLoadBar.init({
   enable_filedownload: true,
  filedownload_anchor_selector: '.js-filedownload'
});
...
...
<a class="js-filedownload" href="...">Download file</a>
...
```

### Requirements ###
jQuery 1.8+

### Installation ###
1. Include the js and css files on the `<head>` of your document.
2. Immediatelly after the `<body>` tag, initialize the library

### Configuration ###
To change the default options of the library, pass the following settings to the .init function.

```javascript
window.CrossPageLoadBar.init({
  //The initial opacity of the loading bar container
  container_opacity: 1,

  //The opacity to fade into, when loading is complete
  fadeto_opacity: 0.1,

  //Enable cross page loading support
  enable_crossload: true,

  //Enable jquery ajax support
  enable_ajax: false,

  //Enable pjax support
  enable_pjax: false,

  //Enable file download support
  enable_filedownload: false,

  //Set a selector for identifying file download links
  filedownload_anchor_selector: null,

  //Milliseconds of the file download grow effect
  downloadfile_msec: 1500,

  //Milliseconds to wait before the bar is displayed
  idle_msec: 1500,

  //The speed of the fadeout effect in milliseconds
  fadeout_msec: 1000,

  //The speed of the bar growing effect in milliseconds
  inc_msec: 6000
});
```

### Example ###

Check out this [demo page](http://nbasili.github.io/crosspageloadbar/) to see it in action. Or try it like this:

```html
<html>
  <head>
    <link media="screen" href="crosspageloadbar.css" type="text/css" rel="stylesheet" />
    <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script>
    <script type="text/javascript" src="crosspageloadbar.js"></script>
  </head>
  <body>
    <script type="text/javascript">
      (function() {
        window.CrossPageLoadBar.init({
          enable_crossload: true,
          enable_pjax: true,
          enable_ajax: true
        });
      })();
    </script>
    <div>
      Content...
    </div>
  </body>
</html>
```
