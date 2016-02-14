Want extremely high resolution images out of google maps? Well, just give your map enormous coordinates and tell [PhantomJS](http://phantomjs.org/) to render it for you.

The phantom js script is pretty simple. Just open the page and call render after giving it some time to load all the map tiles.

```js
var page = require('webpage').create();
page.open('http://localhost:8000/', function() {
  window.setTimeout(function() {
    page.render('nyc3.png');
    phantom.exit();
  }, 60000)
});
```
Just pass the filename of this script to the phantomjs executable.

    $ phantomjs screenshot.js

A simple google maps page, for reference:

```html
<!DOCTYPE html>
<html>
  <head>
    <style type="text/css">
      html, body { height: 100%; margin: 0; padding: 0; }
      #map { width: 5760px; height: 10240px; }
      /*#map { height: 100%; }*/
    </style>
  </head>
  <body>
    <div id="map"></div>
    <script type="text/javascript">

var map;
function initMap() {
  map = new google.maps.Map(document.getElementById('map'), {
    // center: {lat: 41.240553, lng: -95.993235},
    // center: {lat: 41.261612, lng: -95.995023}, // omaha
    // center: {lat: 47.680253, lng: -122.319750}, // seattle
    // center: {lat: 47.610107, lng: -122.333600}, // seattle
    // center: {lat: 35.473963, lng: -83.920715}, // tail of the dragon
    // center: {lat: 18.233597, lng: -66.475986}, // puerto rico
    // center: {lat: -42.551352, lng: -72.792541}, // chile
    // center: {lat: -42.550931, lng: -72.810}, // chile
    center: {lat: 40.682813, lng: -73.975463}, // nyc (barclays)
    zoom: 15,
    mapTypeId: google.maps.MapTypeId.SATELLITE,
    disableDefaultUI: true
  });
}

    </script>
    <script async defer
      src="https://maps.googleapis.com/maps/api/js?key=API_KEY_HERE&callback=initMap">
    </script>
  </body>
</html>
```

