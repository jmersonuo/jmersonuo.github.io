<img src="Images/logo.png">

<h2 align="center"> Mapping opioid-related prescriptions and overdose rates in the U.S. </h2>
<h3 align="center"> Part II: Adding interactivity to web maps through GL-JS </h3>


### In this tutorial you will:


- Publish a map style without adding layers
- Learn about GL-JS and adding interactivity
- Call on map layers using GL-JS
- Learn additional tools and tricks for creating compelling maps

A few additional resources for Mapbox GL JS:

- [https://www.mapbox.com/mapbox-gl-js/api/](https://www.mapbox.com/mapbox-gl-js/api/)
- [https://www.mapbox.com/mapbox-gl-js/examples](https://www.mapbox.com/mapbox-gl-js/examples) 
- Example finished maps that use Mapbox GL JS for more design control and interactivity: [https://native-land.ca/](https://native-land.ca/) or [https://www.mapbox.com/amnesty/](https://www.mapbox.com/amnesty/) or [https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html) 
- This exercise is based on: [https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/](https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/)


----------

### Get started

To create a web map, you'll need to have some familiarity with HTML, CSS, and JavaScript. If you are new to web maps, explore our [tutorials](https://docs.mapbox.com/help/tutorials/) and [documentation](https://docs.mapbox.com/help/how-mapbox-works/web-apps/) to help you get started.
Here’s what you’ll need to get started:

- [Github account](https://github.com/join)
- [JSFiddle Text Editor](https://jsfiddle.net/)

*This is a very beginner intro by a non-developer - there’s a lot more to learn about developing more complex web apps and sites, but we’re focusing just on a simple web map. For more complex projects and teams, you’ll want to learn more about version control and using Github properly, with pull requests etc.*

----------


### Orientation to your tools


For this lesson, we will be using a program called JSFiddle. You can sign up for a free acount at: [https://jsfiddle.net/](https://jsfiddle.net/)
JSFiddle is a simple tool for building and testing code for web development. We recommend using JSFiddle in a Chrome browser
For simplicity, we recommend that you change the editor layout settings in JSFiddle to display by ‘tabs’


<p align="center">
<img src="Images/jsfiddle-tabs.gif">
</p>


----------


### Writing your first code


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 

```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Display a map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>
<body>

<div id='map'></div>
<script>
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
    center: [-74.50, 40], // change long/lat to -98.349609375, 39.095962936305476
    zoom: 9 // Change the zoom to 3!
});
</script>

</body>
</html>
```


1. Copy [this sample code](https://www.mapbox.com/mapbox-gl-js/example/simple-map/) and paste it into the **HTML section** of your JSFiddle.
2. Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/) in row 18 (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).
3. Click ‘Run’ in the upper left


<p align="center">
<img src="Images/changes_map1.png">
</p>


4. Add a title and description and hit save!

5. See your map in fullscreen: Grab your JSFiddle unique ID (url), paste it into a new tab and add `/show` to the end. For example: ‘https://jsfiddle.net/4up1vwsm/show’


 **You’ve just made a web map! Not too shabby!**

<p align="center">
<img src="Images/fistbump.png">
</p>


----------

### Editing your code

Now that we’ve initialized the webmap, let’s try to make some changes to our code. Currently, your map is centered on New Jersey when it loads. We need to change the location and the zoom level so that we can view the entire contiguous United States. 

1. Locate the line of code that is telling the map where to center the view.
2. Try changing the center location to the center of the US by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0) (or looking at the bottom of the right-hand panel in the Mapbox Studio style editor).
3. Change the coordinates in your code and run your changes.
4. Change the zoom level to 3. 
5. Click ‘Run’ to see the changes to your map. 


<p align="center">
    <img src="Images/Screen%20Shot%202019-10-02%20at%2012.06.47%20PM.png">
    </p>

----------

### Adding your custom style

**Style**: The map loads a style via the URL mapbox://styles/mapbox/streets-v11. This is a URL to a remote file that the map will download to determine the [tilesets](https://docs.mapbox.com/help/glossary/tileset/) it includes and how they are styled for the end-user. Mapbox GL JS permits URLs instead of literal data in several places, including data sources. To load the style that you created in the previous assignment, you need to go to go your Mapbox Studio account and find your Style URL ([how to find your Style URL](https://docs.mapbox.com/help/glossary/style-url/)):


<p align="center">
    <img src="Images/mapstyle.png">
    </p>
<br></br>
<h3 align ="center"> OR </h3>
<br></br>
<p align="center">
    <img src="Images/mapstyle.gif">
    </p>


- Edit the row with the style URL it in your code and run your changes. *(Which row to edit? Look for a row with something that looks similar to your style URL)*

<p align="center">
    <img src="Images/Screen%20Shot%202019-10-02%20at%2012.59.27%20PM.png">
    </p>

----------

## Add navigation controls

Let’s try modifying the code to add a new element to the map. Currently, you can zoom in and out using your mouse, but we want to add navigation controls (zoom in, zoom out, and north arrow) to make the zooming functions more obvious to our end users.

To get started, check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)

What part of the example is missing for your current code? Copy and paste the navigation control function into your code after your `var = map` element but before the ```</script>``` and click ‘Run’ when you have finished.  

```

mapboxgl.accessToken = 'YOUR ACCESS TOKEN';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'YOUR STYLE ID', // stylesheet location
    center: [-98.349609375, 39.095962936305476], // change long/lat to -98.349609375, 39.095962936305476
    zoom: 3 // Change the zoom to 3!
});

// Add zoom and rotation controls to the map.
map.addControl(new mapboxgl.NavigationControl());


</script>

</body>
</html>
```

----------

### Adding a dynamic legend

The map that we styled in studio displayed information about overdose rates by state and opioid prescribing rates by county. When we created our style, we set the dynamic zoom levels so that the state level data would appear at zoom level (X) and the county data would appear at zoom level (X).  We want to add a legend for each data layer depending on zoom level. In order do this, we are going to modify the following [code](https://docs.mapbox.com/mapbox-gl-js/example/updating-choropleth/). 

Copy and paste the following just after the opening ``<body>`` tag in your code: 

```
<style>

.legend {
background: rgba(255, 255, 255, 0.9);
border-radius: 3px;
bottom: 30px;
box-shadow: 0 1px 2px rgba(0,0,0,0.10);
font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;
padding: 10px;
position: absolute;
right: 10px;
z-index: 1;
}
 
.legend h4 {
margin: 0 0 10px;
}
 
.legend div span {
border-radius: 50%;
display: inline-block;
height: 10px;
margin-right: 5px;
width: 10px;
}

</style>
```

Next, after your ```<div id='map'></div>``` but before your ```<script> ``` tag, copy and paste the following code: 

```
    <div id='map'></div>
    <div id='state-legend' class='legend'>
      <h4>Overdose Rates </h4>
      <div><span style='background-color: #e9d3d3'></span>6.9 to 11.0</div>
      <div><span style='background-color: #f5c0ad'></span>11.1 to 13.5</div>
      <div><span style='background-color: #f0a184'></span>13.6 to 16.0</div>
      <div><span style='background-color: #cc6f61'></span>16.1 to 18.5</div>
      <div><span style='background-color: #c44936'></span>18.6 to 21.0</div>
      <div><span style='background-color: #911e0d'></span>21.1 to 57.0</div>
    </div>

    <div id='county-legend' class='legend' style='display: none;'>
      <h4>Opioid Prescribing <br> Drug Rates</h4>
      <div><span style='background-color: #ffe9bd'></span>&lt; 57.2</div>
      <div><span style='background-color: #ff8a73'></span>57.2 – 82.3</div>
      <div><span style='background-color: #e13731'></span>82.4 – 112.5</div>
      <div><span style='background-color: #650511'></span>&gt; 112.5</div>
      <div><span style='background-color: #ffffff'></span>Missing Data</div>
    </div>

```

Once you’ve added the above elements to your script, hit ‘Run’ and see what happens. 

The legend for the state data has been initialized but when you zoom into your county level data, the legend doesn’t change to match the county level data. This is because we haven’t yet written any code to tell the map to change legend displays at various zoom levels. To add zoom level controls, you first need to set a zoom level threshold. 

Add a new variable called zoomThreshold below your zoom variable. Set the new zoomThreshold variable to 5. 
var zoomThreshold = 5;

```
      var zoomThreshold = 5;

```

Next, add the following code below your zoomThreshold variable but before your closing ``</script>`` tag (hit ‘Run’ when you are finished): 

```
      var stateLegendEl = document.getElementById('state-legend');
      var countyLegendEl = document.getElementById('county-legend');
      map.on('zoom', function() {
        if (map.getZoom() > zoomThreshold) {
          stateLegendEl.style.display = 'none';
          countyLegendEl.style.display = 'block';
        } else {
          stateLegendEl.style.display = 'block';
          countyLegendEl.style.display = 'none';
        }
      });
 ```     
 
 
 Hit run to see your changes!
 
 <p align="center">
    <img src="Images/Finished-map.gif">
    </p>

----------

### Create your webpage

1. Create a new folder for this map
2. **Create a new file** called index.html
3. In the blank index.html file, paste in the entire code we built in JSFiddle
4. Push it to your webspace

```
<!DOCTYPE html>
<html>

  <head>
    <meta charset='utf-8' />
    <title>Display a map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.css' rel='stylesheet' />
    <style>
      body {
        margin: 0;
        padding: 0;
      }

      #map {
        position: absolute;
        top: 0;
        bottom: 0;
        width: 100%;
      }

    </style>
  </head>

  <body>

    <style>
      .legend {
        background: rgba(255, 255, 255, 0.9);
        border-radius: 3px;
        bottom: 30px;
        box-shadow: 0 1px 2px rgba(0, 0, 0, 0.10);
        font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;
        padding: 10px;
        position: absolute;
        right: 10px;
        z-index: 1;
      }

      .legend h4 {
        margin: 0 0 10px;
      }

      .legend div span {
        border-radius: 50%;
        display: inline-block;
        height: 10px;
        margin-right: 5px;
        width: 10px;
      }

    </style>
    <div id='map'></div>
    <div id='state-legend' class='legend'>
      <h4>Overdose Rates </h4>
      <div><span style='background-color: #e9d3d3'></span>6.9 to 11.0</div>
      <div><span style='background-color: #f5c0ad'></span>11.1 to 13.5</div>
      <div><span style='background-color: #f0a184'></span>13.6 to 16.0</div>
      <div><span style='background-color: #cc6f61'></span>16.1 to 18.5</div>
      <div><span style='background-color: #c44936'></span>18.6 to 21.0</div>
      <div><span style='background-color: #911e0d'></span>21.1 to 57.0</div>
    </div>

    <div id='county-legend' class='legend' style='display: none;'>
      <h4>Opioid Prescribing <br> Drug Rates</h4>
      <div><span style='background-color: #ffe9bd'></span>&lt; 57.2</div>
      <div><span style='background-color: #ff8a73'></span>57.2 – 82.3</div>
      <div><span style='background-color: #e13731'></span>82.4 – 112.5</div>
      <div><span style='background-color: #650511'></span>&gt; 112.5</div>
      <div><span style='background-color: #ffffff'></span>Missing Data</div>
    </div>

    <script>
      mapboxgl.accessToken = 'YOUR MAPBOX TOKEN';
      var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'YOUR STYLE SHEET', // stylesheet location
        center: [-98.349609375, 39.095962936305476], // change long/lat to -98.349609375, 39.095962936305476
        zoom: 3 // Change the zoom to 3!
      });

      // Add zoom and rotation controls to the map.
      map.addControl(new mapboxgl.NavigationControl());

      var zoomThreshold = 5;
      var stateLegendEl = document.getElementById('state-legend');
      var countyLegendEl = document.getElementById('county-legend');
      map.on('zoom', function() {
        if (map.getZoom() > zoomThreshold) {
          stateLegendEl.style.display = 'none';
          countyLegendEl.style.display = 'block';
        } else {
          stateLegendEl.style.display = 'block';
          countyLegendEl.style.display = 'none';
        }
      });

    </script>

  </body>

</html>
```

***Voila! Now you have a live website with your map!*** 

<p align="center">
    <img src="https://media.giphy.com/media/Bj2UZgqqzUxwc/giphy.gif">
    </p>

**Polishing steps:**

- Currently, the tab for your webpage in your browser says ‘Display a map’ - let’s give it a better title - can you see where in the code to change that?

- Change it in your code, and update your webpage.



