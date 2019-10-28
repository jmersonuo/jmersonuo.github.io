<img src="../Images/logo.png" width="150px">


<h2 align="center"> Mapping renters vs owners in Portland </h2>
<h3 align="center"> Part III: Creating a comparitive choropleth map </h3>

The US Census makes owner/renter information readily available for census block geometries, in this lab series we are going to view the owner/renter information in different ways: 

1) Mapping the per-person level information, and 
2) Viewing the relative incidence of owners to renters using a choropeth map. 

For this first exercise, we will be creating two choropleth maps that display 1) the percentage of owners, and 2) the percentage of renters in Portland, Oregon. 

<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/slide.gif">
</p>
  

### In this tutorial you will:

- [Add data](https://www.mapbox.com/help/uploads/) to Mapbox
- Call on map layers using GL-JS
- Learn about GL-JS and adding interactivity, styling your layers 
- Learn additional tools and tricks such as how to [swipe between maps](https://docs.mapbox.com/mapbox-gl-js/example/mapbox-gl-compare/)

----------

### Get started

To create a web map, you'll need to have some familiarity with HTML, CSS, and JavaScript. If you are new to web maps, explore our [tutorials](https://docs.mapbox.com/help/tutorials/) and [documentation](https://docs.mapbox.com/help/how-mapbox-works/web-apps/) to help you get started.

----------

### Data

Download the data below. If your browser opens it, instead of downloading, right-click and use “save-data-as”, to save it to your R-Drive space.

- [Percentage of renters, owners and total population by block group 2017](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Data/Owner-Renter-Pop.geojson) - [Source: US Census](https://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml) 


----------

### Upload data as a tileset to Mapbox

To add the percentage of renters vs owners data to Mapbox as a tileset, you need to upload it to your account. Go to your [**Tilesets**](https://studio.mapbox.com/tilesets/) page in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the geojson data containing your renters and owners data and upload it to your account. 

<p align="center">
  <img src="Images/tilesets.png">
  </p>


<br>

In the last few tutorials we used Studio to dynamically style all of our layers. For this tutorial, we will be using one of Mapbox's custom styles and writing our styling rules directly in our code. 

----------

### Initializing the map!


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a web map in JSFiddle. 

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Swipe between maps</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.1/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.1/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>
<body>

<style>
body {
    overflow: hidden;
}

body * {
   -webkit-touch-callout: none;
     -webkit-user-select: none;
        -moz-user-select: none;
         -ms-user-select: none;
             user-select: none;
}


.map {
    position: absolute;
    top: 0;
    bottom: 0;
    width: 100%;
}
</style>

<script src='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.js'></script>
<link rel='stylesheet' href='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.css' type='text/css' />

<div id='owners' class='map'></div>  //owners map div
<div id='renters' class='map'></div> //renters map div


<script>
  //add your Mapbox access token and map variable here!
</script>

</body>
</html>
```

Notice that there are script and link tags referencing mapbox-gl-compare. This is the Mapbox GL JS [swipe map plugin](https://github.com/mapbox/mapbox-gl-compare).

```html
<script src='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.js'></script>
<link rel='stylesheet' href='https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-compare/v0.1.0/mapbox-gl-compare.css'
```

      
Next, between your script tags (where it says 'add your Mapbox access toke and map variable here') add your Mapbox access token and initialize your owner choropleth by creating a ownerMap variable. This first map will display information about the percentage of homeowners in Portland. 

```JavaScript

mapboxgl.accessToken = 'YOUR ACCESS TOKEN';
  
var ownerMap = new mapboxgl.Map({
    container: 'owners', // owners map div 
    style: 'mapbox://styles/mapbox/dark-v10', // Mapbox dark style 
    center: [0, 0], // change the long/lat coordinates to -122.67745971679688, 45.52751668442124],
    zoom: 0 // change the zoom level to 10 
});
```

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/full-mapp.png">
  </p>



Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/)in the section that says "ACCESS TOKEN GOES HERE" (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).

The Mapbox style has already been initialized for you. In this exercise we are using the Mapbox dark style.  



----------

### Changing the map location and zoom level 

Now that we’ve initialized the webmap, let’s try to make some changes to our code. Currently, your map is zoomed out to see the whole world when it loads. We need to change the location and the zoom level so that we can only view Portland, Oregon. 

1. Locate the line of code that is telling the map where to center the view.
2. Try changing the center location to the center of the US by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0).
3. Change the coordinates in your code and preview your changes.
4. Change the zoom level to 10. 
5. Preview your map in a browser to view your changes.


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Portland.png">
  </p>



----------

### Add a second map variable 

Below your ownerMap variable, initialize your renter map by creating a new variable called renterMap. This second map will display information about the percentage of renters in Portland. 

```javascript 
  
var renterMap = new mapboxgl.Map({
    container: 'renters', // owners map div 
    style: 'mapbox://styles/mapbox/dark-v10', // Mapbox dark style 
    center: [-122.67745971679688, 45.52751668442124], 
    zoom: 10 
});
```

----------

### Comparing maps

Next, we need to enables users to compare our two maps by swiping left and right. Do this add the following code after your two map variables. Check out [this GitHub repo](https://github.com/mapbox/mapbox-gl-compare) for more information about the mapbox-gl-compare plugin.

```JavaScript 

var map = new mapboxgl.Compare(ownerMap, renterMap, {
});

```

Preview your map in a browser to view your changes.



<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/compare1.png">
  </p>



### The load event

What is a callback?

Initializing the map on the page does more than create a container in the map div. It also tells the browser to request the Mapbox Studio style. This can take variable amounts of time depending on how quickly the Mapbox server can respond to that request, and everything else you're going to add in the code relies on that style being loaded onto the map. As such, it's important to make sure the style is loaded before any more code is executed.

Fortunately, the map object can tell your browser about certain events that occur when the map's state changes. One of these events is load, which is emitted when the style has been loaded onto the map. Through the map.on method, you can make sure that none of the rest of your code is executed until that event occurs by placing it in a callback function that is called when the load event occurs.

To make sure the rest of the code can execute, it needs to live in a callback function that is executed when the map is finished loading. 

For this exercise you will have two load events, one for your owner map and one for your renter map. 

```JavaScript 

ownerMap.on('load', function() {
  // the rest of the owner data code will go in here
});

```

Next, we will add our owner and renter data layer to the map using ownerMap.addLayer(). Remember that this goes inside of the load function. 


```JavaScript

       ownerMap.addLayer({
         id: 'Owner Data',
         type: "fill",
         source: {
           type: 'vector',
           url: 'mapbox://YOUR URL' //input your tileset url
         },
           'source-layer': 'YOUR SOURCE LAYER NAME', //input your source layer name e.g. Owner-Renter-Pop-dr7310
         paint: {
           'fill-color': '#cb1515',
         }

       });

```

Before you preview your changes, you will need to make some changes to this code. 

In your Mapbox account, navigate to your **Owner-Renter-Pops** tileset menu. 

#### Tileset Menu 

For each tilset, you can either click on the name of the tilset to go to its information page or click the button <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Screen%20Shot%202019-10-25%20at%202.20.03%20PM.png"> for more options: 

**Replace**
Replace the current data in your tileset with new data. The tileset ID will stay the same and the new data will be reflected in all styles that reference this tileset.

**Delete**
You can permanently delete a tileset from your account at any time. Deleted tilesets may not be recovered.

**Tileset ID**
From this menu, you can also copy the [tileset ID](https://docs.mapbox.com/help/glossary/tileset-id/) to be used with Mapbox SDKs and APIs.


Copy your tileset ID and add it to your code (be sure to keep the mapbox:// in your url):  

```url: 'mapbox://YOUR URL' //input your tileset url```

Next, copy and paste the name of your [source layer](https://docs.mapbox.com/help/glossary/source-layer/) into the code. 

Preview your map in a browser to view your changes! You should see your vector layer on your map. 


<p align='center'>
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Screen%20Shot%202019-10-25%20at%202.25.13%20PM.png">
  </p>
  
### Data driven styling 

You can assign a color to each block group based on its field and variables. For our first map, we want to create a choropleth map that displays the percentage of the Portland population that owns a home. In order to style by homeownership, you will need to style our data by our 'Own' field and to change the 'fill-color' parameter of the layer you just added to your map. 

Replace '#cb1515' with the following: 

```JavaScript
   ["step",
   ["get", "Own"],
   "hsl(225, 100%, 97%)",
   16.81,
   "hsl(203, 47%, 82%)",
   22.338,
   "hsl(202, 57%, 63%)",
   27.32,
   "#3182bd",
   31.942,
    "hsl(210, 90%, 32%)"],
   "fill-opacity": 0.7
                
 ```
 
This code is very similar to the process we used in Studio. We are filtering the data from our layer by the data range found in the 'Own' field. Each of the five steps is assigned a color and the fill-opacity is set to 0.7. 

Preview your map in a browser to view your changes.

<p align='center'>
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/owner_slide.png">
  </p>
  

### Adding a second layer 

Currently, we have only have information for homeowners displayed on our map. In order to make a meaningful comparison, we will need to add information about renters. 

First, add a second load event called renterMap (the renter variable will go inside of this function):

```JavaScript 

renterMap.on('load', function() {
  // the rest of the renter data code will go in here
});

```

Next, add your renter data as a layer using .addLayer. 

```JavaScript
       renterMap.addLayer({
         id: 'Renter Data',
         type: "fill",
         source: {
           type: 'vector',
           url: 'mapbox://YOUR URL' //input your tileset url
         },
           'source-layer': 'YOUR SOURCE LAYER NAME', //input your source layer name e.g. Owner-Renter-Pop-dr7310
         paint: {
           'fill-color': '#cb1515',
         }

       });

```

Copy your tileset ID and add it to your code (be sure to keep the mapbox:// in your url):  

```url: 'mapbox://YOUR URL' //input your tileset url```

Next, copy and paste the name of your [source layer](https://docs.mapbox.com/help/glossary/source-layer/) into the code. Your tileset ID and the source-layer name will be the same for both layers. 

Preview your map in a browser to view your changes! You should see your vector layer on your map. 


### Styling your second layer 

For the renter map, we want to create a choropleth map that displays the percentage of the Portland population that rents. In order to style by percentage of renters, you will need to style our data by the 'Rent' field. You will also need to change the 'fill-color' parameter of the layer you just added to your map. 

Replace '#cb1515' with the following: 

```JavaScript
   ["step",
   ["get", "Rent"],
   "hsl(225, 100%, 97%)",
   16.81,
   "hsl(203, 47%, 82%)",
   22.338,
   "hsl(202, 57%, 63%)",
   27.32,
   "#3182bd",
   31.942,
    "hsl(210, 90%, 32%)"],
   "fill-opacity": 0.7
                
 ```
 
Preview your map in a browser to view your changes.
 
<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/slide.gif">
</p>
  
 
### Congratulations! You've completed the exercise! 

<p align = "center">
	<img src="https://media.giphy.com/media/11uArCoB4fkRcQ/giphy.gif">
	</p>


[Link](https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Population-Choropleth.html) to completed project.

### Extra Steps 

Try adding a legend and a title to your map to make it easier for readers to understand the comparison between owners and renters in Portland. 


