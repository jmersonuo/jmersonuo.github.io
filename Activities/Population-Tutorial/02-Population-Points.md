<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">

<h2 align="center"> Mapping renters vs owners in Portland </h2>
<h3 align="center"> Part II: Adding interactivity to web maps through GL-JS </h3>


### In this tutorial you will:

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
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/jsfiddle-tabs.gif">
</p>


----------


### Writing your first code


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 

```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Owners vs Renters Map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
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
mapboxgl.accessToken = 'ACCESS TOKEN GOES HERE'; 
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'STYLE URL GOES HERE', // stylesheet location
});
</script>

</body>
</html>
```


Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/)in the section that says "ACCESS TOKEN GOES HERE" (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).

----------

### Adding your custom style

**Style**: Mapbox GL JS permits URLs instead of literal data in several places, including data sources. To load the style that you created in the previous assignment, you need to go to go your Mapbox Studio account and find your Style URL ([how to find your Style URL](https://docs.mapbox.com/help/glossary/style-url/)):


<p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/mapstyle.png">
    </p>
<br></br>
<h3 align ="center"> OR </h3>
<br></br>
<p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/mapstyle.gif">
    </p>


- Copy and paste your style URL into your code and hit run to view your changes. *(Which row to edit? Look for a row with something that says something like 'STYLE URL GOES HERE')*

<p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Initial_Map.png">
    </p>

----------

## Add navigation controls

Let’s try modifying the code to add a new element to the map. Currently, you can zoom in and out using your mouse, but we want to add navigation controls (zoom in, zoom out, and north arrow) to make the zooming functions more obvious to our end users.

To get started, check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)

What part of the example is missing for your current code? Add the navigation control function ito your code below your map variable and click ‘Run’ when you have finished.  

```

// Add zoom and rotation controls to the map.
map.addControl(new mapboxgl.NavigationControl());

```

----------

### Adding a dynamic legend

The following code adds the styling rules needed to add a legend to the map. 

Copy and paste the following just after the opening ``<style>`` tag in your code: 

```
 p {
        color: #CCC;
      }

      h4 {
        color: #CCC;
        margin-left: 10px;
      }


      .LegendContainer {
        position: absolute;
        bottom: 20px;
        left: 20px;
        z-index: 2;
        width: 300px;
        height: 40px;
        background: rgba(80, 80, 80, .75);
        transition: width 2s, height 2s;
        border-radius: 7px;
      }

      .descriptionPanel {
        position: absolute;
        bottom: 65px;
        left: 20px;
        z-index: 2;
        width: 300px;
        height: 40px;
        background: rgba(80, 80, 80, .75);
        transition: width 2s, height 2s;
        overflow: hidden;
        border-radius: 7px;
      }

      .LegendContainer:active {
        width: 240px;
        height: 250px;
      }

      .legendItem {
        float: left;
        width: 50%;
        margin-top: 10px;
        margin-bottom: 10px;
      }

      .colorBox {
        width: 20px;
        height: 20px;
        float: left;
        border-radius: 10px;
        margin-left: 10px;
      }

      .layerDescription {
        color: white;
        float: left;
        margin-left: 10px;
      }

      .chevron {
        position: relative;
        margin-left: 45%;
        font-size: x-large;
        color: white;
      }

```

Next, we will need to add a container to display background information about our map and data sources. 

```
     <div class="descriptionPanel" id="descriptionPanel" style="height: 320px;">
      <span onClick=panelSelect() id="glyph" class="chevron glyphicon glyphicon-chevron-down"></span>
      <hr />
      <h4>WHAT AM I LOOKING AT?</h4><br />
      <p style="margin-left: 10px; margin-right: 10px;">
        This is a map showing every single person in the United States as a dot. Data is taken from the 2017 US Census, and is accurate at the level of a block, however within each block location is randomized. Points are colored based on number home owners versus renters on a block.
      </p>
    </div>

```

Create a second container to help your users differentiate between the layer colors. 

```
    <div class="LegendContainer">
      <div class="legendItem">
        <div class="colorBox" style="background-color: hsl(185, 100%, 50%);"></div>
        <div class="layerDescription">Owners</div>
      </div>
      <div class="legendItem">
        <div class="colorBox" style="background-color: hsl(303, 100%, 50%);"></div>
        <div class="layerDescription">Renters</div>
      </div>
    </div>
  ```

Once you’ve added the above elements to your script, hit ‘Run’ and see what happens. 


Next, let's add an interaction to our legend. The following variable and function will enable the user to show and hide the map description that we added in the last section. Copy and paste the code snippet after your map variable: 

```     
      var state = { panelOpen: true };

      function panelSelect(e){
        if(state.panelOpen){
          document.getElementById('descriptionPanel').style.height = '26px';
          document.getElementById('glyph').className = "chevron glyphicon glyphicon-chevron-up";
          state.panelOpen = false;
        } else {
          document.getElementById('descriptionPanel').style.height = '320px';
          document.getElementById('glyph').className = "chevron glyphicon glyphicon-chevron-down";
          state.panelOpen = true;
        }
      }
    
 ```     
 
 Hit run to see your changes!
 
 <p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Population-Tutorial/Images/Screen%20Shot%202019-10-16%20at%202.25.29%20PM.png">
    </p>

----------

### Create your webpage


*You’ve made a web map! But this is just serving the map directly from the code within JSFiddle, it isn’t a webpage yet… to do that we need some way to host a webpage. Today, let’s use Github Pages.*
**Orientation to Github Pages** 

1. (Create a Github account if you don’t have one)
2. Set up a Github [repository](https://help.github.com/articles/create-a-repo/)
    - Name it whatever you want
    - Make it Public
    - Click the box to ‘Initialize this repository with a README’
![](https://lh3.googleusercontent.com/asCZvCmvq6bxNthgMEgDhmq1uQ1IwHqdLYOkGAKpoQT2yEhf_7e8Rsu5doIZ--mvDJ3Ru6h7Qf_rO95LEn9s7spGUnx2xLI7MleSAML0ra6fR1A6jpbx26qfKL9ksWsi74q1P9uC)

3. **Create a new file** called index.html
4. In the blank index.html file, paste in the entire code we built in JSFiddle

```
<!DOCTYPE html>
<html>

  <head>
    <meta charset='utf-8' />
    <title>Owners vs Renters Map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
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

      p {
        color: #CCC;
      }

      h4 {
        color: #CCC;
        margin-left: 10px;
      }


      .LegendContainer {
        position: absolute;
        bottom: 20px;
        left: 20px;
        z-index: 2;
        width: 300px;
        height: 40px;
        background: rgba(80, 80, 80, .75);
        transition: width 2s, height 2s;
        border-radius: 7px;
      }

      .descriptionPanel {
        position: absolute;
        bottom: 65px;
        left: 20px;
        z-index: 2;
        width: 300px;
        height: 40px;
        background: rgba(80, 80, 80, .75);
        transition: width 2s, height 2s;
        overflow: hidden;
        border-radius: 7px;
      }

      .LegendContainer:active {
        width: 240px;
        height: 250px;
      }

      .legendItem {
        float: left;
        width: 50%;
        margin-top: 10px;
        margin-bottom: 10px;
      }

      .colorBox {
        width: 20px;
        height: 20px;
        float: left;
        border-radius: 10px;
        margin-left: 10px;
      }

      .layerDescription {
        color: white;
        float: left;
        margin-left: 10px;
      }

      .chevron {
        position: relative;
        margin-left: 45%;
        font-size: x-large;
        color: white;
      }

    </style>
  </head>

  <body>
    <div class="descriptionPanel" id="descriptionPanel" style="height: 320px;">
      <span onClick=panelSelect() id="glyph" class="chevron glyphicon glyphicon-chevron-down"></span>
      <hr />
      <h4>WHAT AM I LOOKING AT?</h4><br />
      <p style="margin-left: 10px; margin-right: 10px;">
        This is a map showing every single person in the United States as a dot. Data is taken from the 2017 US Census, and is accurate at the level of a block, however within each block location is randomized. Points are colored based on number home owners versus renters on a block.
      </p>
    </div>

    <div class="LegendContainer">
      <div class="legendItem">
        <div class="colorBox" style="background-color: hsl(185, 100%, 50%);"></div>
        <div class="layerDescription">Owners</div>
      </div>
      <div class="legendItem">
        <div class="colorBox" style="background-color: hsl(303, 100%, 50%);"></div>
        <div class="layerDescription">Renters</div>
      </div>
    </div>


    <div id='map'></div>
    <script>
      mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
      var map = new mapboxgl.Map({
        container: 'map', // container id
        style: 'mapbox://styles/mjdanielson/ck1tk2eh06dar1cnl4fcaudr1', // stylesheet location
      });

      map.addControl(new mapboxgl.NavigationControl());

      var state = {
        panelOpen: true
      };

      function panelSelect(e) {
        if (state.panelOpen) {
          document.getElementById('descriptionPanel').style.height = '26px';
          document.getElementById('glyph').className = "chevron glyphicon glyphicon-chevron-up";
          state.panelOpen = false;
        } else {
          document.getElementById('descriptionPanel').style.height = '320px';
          document.getElementById('glyph').className = "chevron glyphicon glyphicon-chevron-down";
          state.panelOpen = true;
        }
      }

    </script>

  </body>

</html>

```

5. [Enable Github Pages](https://pages.github.com/) (in repo Settings - the gear symbol in the upper right):
6. Then wait a minute, then go to your Github page address (https://[YOUR GITHUB NAME].github.io/[YOUR REPO NAME]/) - you can find this by scrolling back to the Github Pages settings.
7. (You might need to wait another minute if it doesn’t work right away)

***Voila! Now you have a live website with a Mapbox map!*** 

<p align="center">
    <img src="https://media.giphy.com/media/Bj2UZgqqzUxwc/giphy.gif">
    </p>

**Polishing steps:**

- Change it in your code, commit your changes in your Github index.html file, give it a minute, and check your webpage.




