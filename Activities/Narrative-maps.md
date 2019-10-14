## Making Fixed and Fly-To Maps

Today we are going to make two differnt types of map. The first will be fixed in place. It can't be panned or zoomed by the user. The second will automatically fly-to predefined locations, guiding the user around.

### I. Preparing your page

As usual, you need to do the following preparation steps on your page (this time we are adding version 1.4.0:

* Include Mapbox JavaScript file:

```html
      <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.js'></script>
    
```

* Include Mapbox CSS file __after__ Mapbox’s JavaScript:

```html
      <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.css' rel='stylesheet' />
```

In the body, put a title ("Map 1:"), a div element with the id "map1" where you want your first map to be, and a line below the map:

```html
<h1> Map 1: </h1>
<div id='map1'></div>
<hr>
```

This time we will apply some CSS to specify the height and width of the map. This is particularly important for the map div, which *won't* show up on the page until you give it a height:

```css
        body { margin:50px; padding:0; }
        #map { position:relative; height:300px; width:50%;}
```

This means the body div of your web page has a 50px margin around the edge, and the div with the ID "map", will be 300px tall, and will take 50% of the width of your browser page.

Now you’re ready to initialize the map and customize it.

### II. Setting up the fixed map

Let’s create a map of the centered on Portland with the Mapbox Streets style. Note: all the following code should be between script tags.

Add your access token. Without this, the mapbox code will not work. 

```javascript
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
```

Remember, you can find your access tokens, create new ones, or delete existing ones on your [Access Tokens page](https://account.mapbox.com/access-tokens/) or programmatically using the [Mapbox Tokens API](https://docs.mapbox.com/api/accounts/#tokens)._

Next, we’ll initialize the map and set its view with specified coordinates and a zoom level.

<p align="center">
    <img src= "Images/01_Portland.png">
</p>
 
In the code block below, you will need to replace:
1. the style URL:  'mapbox://styles/mapbox/streets-v11' check out the map [API](https://docs.mapbox.com/mapbox-gl-js/api/#map) to see review the style options 
2. the coordinates for the starting position. Use Portland, Oregon: [-122.6788, 45.5212]

```javascript
var map = new mapboxgl.Map({
    container: 'map', // id of a div on your page, where the map will be inserted
    style: 'set-the-style-here', // the style URL 'mapbox://styles/mapbox/streets-v11' 
    center: [set-the-lng, set-the-lat], // starting position [lng, lat] eg. [-122.6788, 45.5212]
    zoom: 11 // starting zoom 
});
```

Your map should be ready to take a look at. Open your `.html` file in a browser and take a look.
No map? There is likely an error in your code. Open your browser's **Developer tools or Web Console** to look for error messages.
Can you pan and zoom? Great.

### III. Add a marker with a popup

Like last time, let’s add a marker to the same longitude/latitude that we centered our map on. Remember you can look at the [API](https://docs.mapbox.com/mapbox-gl-js/api/#marker) to see what marker options are available.

Add the script:

```javascript
            var popup = new mapboxgl.Popup()
                .setText('This is my first point.');

            var marker = new mapboxgl.Marker({color:'red'})
              .setLngLat([-122.6788, 45.5212]) // starting position [lng, lat]
              .setPopup(popup) //add the popup to the marker 
              .addTo(map);
```
<p align = "center">
    <img src="Images/Portland_Marker.png">
 </p>


### IV. Remove the map interactivity

Let's look at the map API again, specifically at the [interaction handlers](https://docs.mapbox.com/mapbox-gl-js/api/#user%20interaction%20handlers)
Map objects have several interactivity handlers. We are going to disable them all.
After the was initialized, add the following JavaScript code:

```javascript
            // Disable drag and zoom handlers.
            map.dragPan.disable();
            map.scrollZoom.disable();
            map.boxZoom.disable();
            map.dragRotate.disable();
            map.keyboard.disable();
            map.doubleClickZoom.disable();
            map.touchZoomRotate.disable();
            map.touchZoomRotate.disableRotation();
```

Notice that each line starts with `map`, which is the variable name used when we initialized the map: `var map = new mapboxgl.Map(...`.

### Congratulations! You've made a webpage with two static maps! For your assignment, you'll have to add a third map. 

