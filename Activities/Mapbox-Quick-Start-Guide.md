## Mapbox Quick Start Guide

Please sign up for a mapbox account [here](https://account.mapbox.com/auth/signup/).

This step-by-step guide will quickly get you started on Mapbox basics, including setting up a Mapbox map, working with markers, circles and popups and setting up events! All of the code below can be found in this handy [JSFiddle](https://jsfiddle.net/mjdanielson/9jh3bzc8/1/).

Begin by copying the files for today's activity from the the "Class_Data" folder to your personal workspace on the "R" drive. Open and edit the file using a text editor, such as Brackets. 

### I. Preparing your page

Before writing any code for the map, you need to do the following preparation steps on your page:

* Include Mapbox JavaScript file:

```html
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.js'></script>
    
```

* Include Mapbox CSS file __after__ Mapbox’s JavaScript:

```html
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.css' rel='stylesheet' />
```

Put a div element with a certain id where you want your map to be:

```html
<div id='map'></div>

```

You will also want to apply some CSS to specify what the layout looks like. This is particularly important for the map div, which *won't* show up on the page until you give it a height:

```css
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
```

This means the body div of your web page has 0 margin or padding, and the div with the ID "map", will fill the space 0 pixles from the top, to 0 pixles from the bottom, and 100% of the width of your browser page... resulting in a full page map!

<a title="Felix.leg [CC BY-SA 3.0 (http://creativecommons.org/licenses/by-sa/3.0/)], via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:Css_box_model.svg"><img width="512" alt="Css box model" src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Css_box_model.svg/512px-Css_box_model.svg.png"></a>

Now you’re ready to initialize the map and do some stuff with it.

### II. Setting up the map

Let’s create a map of the centered on Portland with the beautiful Mapbox Streets style. 

The first thing you'll need to do is add your access token. Without this, the rest of the code will not work. Note: all the following code should be between script tags.:

```javascript
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';

```

_To use any of Mapbox's tools, APIs, or SDKs, you'll need a Mapbox [access token](https://docs.mapbox.com/help/glossary/access-token/). Mapbox uses access tokens to associate API requests with your account. You can find your access tokens, create new ones, or delete existing ones on your [Access Tokens page](https://account.mapbox.com/access-tokens/) or programmatically using the [Mapbox Tokens API](https://docs.mapbox.com/api/accounts/#tokens)._


Next, we’ll initialize the map and set its view with specified coordinates and a zoom level.

<p align="center">
    <img src= "Images/01_Portland.png">
  </p>
 

For this section of code, we will need a [style ID](https://docs.mapbox.com/help/glossary/style-id/).  A style ID is a unique identifier for each style associated with any Mapbox username. To use the Mapbox Styles API, you will need to know the style ID for the map style you are working with.

In the code block below, you will need to replace the coordinates for the starting position. Try setting the coordinates for Portland, Oregon by replacing the longitude field witih: -122.6788 and the latitude field with: 45.5212. You can http://geojson.io to find the coordinates by placing a marker using.

```javascript
var map = new mapboxgl.Map({
    container: 'map', // id of a div on your page, where the map will be inserted
    style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
    center: [lng, lat], // starting position [lng, lat] eg. [-122.6788, 45.5212]
    zoom: 11 // starting zoom 
});
```

That’s it! You have a working Mapbox map now. Open your `.html` file in a browser and take a look.

No map? There is likely an error in your code. Open your browser's **Web Console** to look for error messages.

Try changing it:
1. Adjust the zoom level to see how this impacts the map. 
2. Set the center coordinates to two other cities around the world. 

When you have finished experimenting, make sure your code is set to Portland and your zoom level is set to 11 before moving on.

<p align = "center">
<img src = "https://media.giphy.com/media/xT0xezQGU5xCDJuCPe/giphy.gif">
</p>

### III. Adding a marker

Besides a basemap, you can easily add other things to your map, including markers and popups.

Let’s add a marker to the same longitude/latitude that we centered our map on:

```javascript
var marker = new mapboxgl.Marker()
  .setLngLat([replace with longitude, replace with latitude]) // starting position [lng, lat] 
  .addTo(map);
```

<p align = "center">
    <img src="Images/Portland_Marker.png">
 </p>

Take a look at the [API](https://docs.mapbox.com/mapbox-gl-js/api/#marker) to see what marker options are available.

Let's change the color of our marker! The default color for the marker is blue. Add a color parameter to your code and change the color! You can use the name of most common colors (`'red'`, `'blue'`, `'green'`) or enter a HEX colod code (`'#42f569'`) or rgb color (`'rgb(0,255,0)'`). We'll cover colors in more detail soon. Try a few different colors.

```javascript
var marker = new mapboxgl.Marker({color:'red'})
  .setLngLat([-122.6788, 45.5212]) // starting position [lng, lat] 
  .addTo(map);
```

Want to add antother marker? Create a second marker variable.

```javascript
var marker2 = new mapboxgl.Marker({color:'red'})
  .setLngLat([-122.69, 45.55]) // starting position [lng, lat] 
  .addTo(map);
```


### IV. Working with popups

<p align = "center">
	<img src ="Images/Portland_Markers.png">
</p>

Popups are usually used when you want to attach some information to a particular object on a map. In Mapbox, you can [add a popup](https://docs.mapbox.com/mapbox-gl-js/api/#popup) to your features with only a few lines of code! 

First, you will need to initialize a pop-up variable. In the JavaScript section of your code, make sure you declare this variable **before** you declare the marker variable, which will use it: 

```javascript
var popup = new mapboxgl.Popup({ offset: 25 })
.setHTML('Hello World. Welcome to Portland!');
```

Next add the `.setPopup` function to your existing marker variable:

```javascript
var marker = new mapboxgl.Marker()
    .setLngLat([-122.6788, 45.5212])
    .setPopup(popup) //add the popup to the marker 
    .addTo(map); // add the open marker to the map
```
Once, you added the `.setPopup` function to your marker, refresh your map and click on the marker!


You can also use popups as layers (when you need something more than attaching a popup to an object). Add this code block after your marker:

```javascript
var popup_layer = new mapboxgl.Popup({closeOnClick: false}) 
.setLngLat([-122.64, 45.5]) //popup coordinates
.setHTML('<h1>Hi Portland!</h1>') //popup text
.addTo(map); //add this popup to the map!
```

Try changing the `closeOnClick` argument to 'true' and refresh your map. What happens when you click anywhere in the map? 

Take a look at the [popup](https://docs.mapbox.com/mapbox-gl-js/api/#popup) documentation to learn more about the parameters associated with Mapbox popups. Try adjusting one or more parameters - for instace, try changing the anchor position. 


```javascript
      var popup_layer = new mapboxgl.Popup({
          closeOnClick: true, anchor: 'top-right'
        })
        .setLngLat([-122.64, 45.5])
        .setHTML('<h1>Hi Portland!</h1>')
        .addTo(map);
```

Notice that you can put any HTML tags, as a single string element, within the `setHTML` functions. For example, you could add an [image](https://www.w3schools.com/html/html_images.asp) or a [hyperlink](https://www.w3schools.com/html/html_links.asp).
Keep in mind, since you need to add a single string element, you'll have to carefully nest any quotation marks.

```javascript
    var popup_layer_voodoo = new mapboxgl.Popup({
          closeOnClick: true, anchor: 'top-left'
        })
        .setLngLat([-122.673308, 45.522675])
        .setHTML('<a href="https://www.voodoodoughnut.com">voodoo donuts</a>')
        .addTo(map);
```


### Congratulations! You've completed the exercise! 

<p align = "center">
	<img src="https://media.giphy.com/media/11uArCoB4fkRcQ/giphy.gif">
	</p>

