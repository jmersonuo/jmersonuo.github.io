<img src="Images/logo.png" width="150px">

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

----------


### Writing your first code


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map. Create a new folder for this assignment on your *R-drive*. Create a new file called `index.html` and copy the code below.

```html
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


- Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/)in the section that says "ACCESS TOKEN GOES HERE" (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).

----------

### Adding your custom style

**Style**: Mapbox GL JS permits URLs instead of literal data in several places, including data sources. To load the style that you created in the part 1, you need to go to go your Mapbox Studio account and find your Style URL ([how to find your Style URL](https://docs.mapbox.com/help/glossary/style-url/)):

<p align="center">
    <img src="../Opioid-Tutorial/Images/mapstyle.gif">
</p>
<br>
<h3 align ="center"> OR </h3>
<br>
<p align="center">
    <img src="../Opioid-Tutorial/Images/mapstyle.png">
</p>

- Copy and paste your style URL into your code. *(Look for a row with something that says something like 'STYLE URL GOES HERE')*
<p align="center">
    <img src="Images/Initial_Map.png">
    </p>

Now preview it in a browser to view your changes. Is is blank? Did you add _your_ mapbox token and your style?

----------

## Add navigation controls

Let’s try modifying the code to add a new element to the map. Currently, you can zoom in and out using your mouse, but we want to add navigation controls (zoom in, zoom out, and north arrow) to make the zooming functions more obvious to our end users.

To get started, check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)

What part of the example is missing for your current code? The NavigationControl! Add the navigation control function into your code below your map variable. This goes before the closing `</script>` tag. Pay attention to the whitespace as you add new code. Keep the whitespace neat!

Preview it in the browser when you have finished. See the nav controls on the top right?

Are you an advanced programmer? look in the API reference for [nagivgation control](https://docs.mapbox.com/mapbox-gl-js/api/#navigationcontrol) to see how to move the control to the `top-left`.

_Hint:_ The example in the documentation adds the control in two lines, whereas we had previously added it in one line. 

```javascript
// Add zoom and rotation controls to the map.
map.addControl(new mapboxgl.NavigationControl());

```

----------

### Adding a dynamic legend

The following code adds the *styling rules* that will be style the 
DOM objects that show the legend for the map. 

This is CSS. Copy and paste the following just after the opening ``<style>`` tag in the `<head>` of your code: 

```css
      /*  stlye for paragraph tags */
      p {
        color: white; 
      }

      /* style for heading level 4 tags */
      h4 { 
        color: white;
        margin-left: 10px;
      }

      /*  style for items with the class "LegendContainer" */
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

      /*  style for items with the class "descriptionPanel" */
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

      /*  style for items with the class "descriptionPanel" when active */
      .LegendContainer:active {
        width: 240px;
        height: 250px;
      }

      /* style for items with the class "legendItem" */
      .legendItem {
        float: left;
        width: 50%;
        margin-top: 10px;
        margin-bottom: 10px;
      }

      /* style for items with the class "colorBox" */
      .colorBox {
        width: 20px;
        height: 20px;
        float: left;
        border-radius: 10px;
        margin-left: 10px;
      }

      /* style for items with the class "layerDescription" */
      .layerDescription {
        color: white;
        float: left;
        margin-left: 10px;
      }

      /* style for items with the class "chevron" */
      .chevron {
        position: relative;
        margin-left: 45%;
        font-size: x-large;
        color: white;
      }

```

Next, we will need to add a container to display background information about our map and data sources. Add a new DIV container to your DOM by adding this code below the map DIV container. Add a comment above this code explaining what it is.

```html
     <div class="descriptionPanel" id="descriptionPanel" style="height: 320px;">
        <span onClick=panelSelect() id="glyph" class="chevron glyphicon glyphicon-chevron-down"></span>
        <hr />
        <h4>WHAT AM I LOOKING AT?</h4><br />
        <p style="margin-left: 10px; margin-right: 10px;">
        This is a map showing every single person in the United States as a dot. Data is taken from the 2017 US Census, and is accurate at the level of a block, however within each block location is randomized. Points are colored based on number home owners versus renters on a block.
        </p>
     </div>

```

Take a look at your map. See the new container!?
<br><br>
Create a second container to help your users differentiate between the layer colors. Add a comment above this code explaining what it is.

```html
  <div class="LegendContainer">
    <div class="legendItem">
        <div class="colorBox" style="background-color: #00d2e6;"></div>
        <div class="layerDescription">Owners</div>
    </div>
    <div class="legendItem">
        <div class="colorBox" style="background-color: #cc00c2;"></div>
     <div class="layerDescription">Renters</div>
  </div>
  ```
<br>
Take a look at your changes! Blank? Check your bowser's console for errors.

**Recap:** To create the legend, we added several DOM Objects using DIVs and Spans using HTML. The "style" of these objects was set using CSS. The CSS was used to make legend object float in front of the map. A legend could also be fixed above, below, or beside the map. The colors of the dots in the legend were hard coded to match the colors we used in the map in the HTML above. If you change the colors in your style, you'll _also_ have to change them in the legend.

<hr>
<br>
Next, let's add interaction to our legend. For this we need to add some JavaScript. The following variable 'state' and function 'panelSelect' will enable the user to show and hide the map description that we added in the last section. Copy and paste the code snippet after your map variable. Add a comment above to indicate what this is for (e.g. // legend interatcion).

```javascript
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
 
Take a look at your changes in a browser once again! Is it interactive? <br>
Yes? Nice.


----------

### Create your webpage

Copy the file to your "Pages" webspace to see it working live.  

***Voila! Now you have a live website with a Mapbox map!*** 

If you don't follow how every line of code works, that's OK! At this point it is important to understand that you added several chunks for code. Some for the map, some for the legend, and some for interactivity. You could add your own data to a Mapbox Style, add that style to this map, make a few changes to the legend and you can make this interactive map your own!

<p align="center">
    <img src="https://media.giphy.com/media/Bj2UZgqqzUxwc/giphy.gif">
</p>




