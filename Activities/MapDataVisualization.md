## Creating map-based data visualizations

This tutorial shows you how to create various map data visualizations using the Data visualization component in the Mapbox Studio style editor. This has been adapted from a tutorial published by Mapbox: [https://docs.mapbox.com/help/tutorials/create-a-map-with-data-visualization-component/](https://docs.mapbox.com/help/tutorials/create-a-map-with-data-visualization-component/)

The **Data visualization component** is a style component that smart-styles a map layer based on the geospatial data in the layer's source. The component creates an initial data visualization, and you can then customize the appearance of the visualization by changing its component style properties.

<p align="center">
    <img src= "Images\dataviz_all.jpg" alt="six examples of map based data visualization">
</p>

For each map in this tutorial you will:

- Create a new style
- Choose some custom data to visualize
- Select a visualization type
- Use built-in component controls to adjust the appearance of your visualization
- Publish your style
- Create a full page map using skills acquired earlier in the course

<br>

### **_I. GETTING STARTED_**

### Step 1: Create a new style

To set up your style, follow these steps:

**Create a new style in the style editor**

1. Go to your [Styles]("https://console.mapbox.com/studio/") page https://console.mapbox.com/studio/
2. Click the **New style** button.
3. Select the `Start from scratch` option.
4. Click `Customize`.

<p align="center">
    <img src= "Images\datavis_createstyle.png" alt="mapbox studio create style page">
</p>

The *Studio style* editor will open, and now you can start prepping your data in the next step.

**Add components to style your blank map**

In the style editor you'll see a blank map, which you will need to add components to get the map to render:

5. Switch the map projection to use Mercator projection:
    - Open the **Global** tab
    - Click Projection
    - Under the Projection Name dropdown, select Mercator
6. Color the basemap:
    - You will need to add the land and water to the style, as follows:
    - Click **Layers** > Add Layer (+) > Components > Land & water.
    - Click any of the landuse layers and set the Base color to #2c2a92.
You should now see a blue map with a mercator projection.


<p align="center">
    <img src= "Images\04_BlueMercator.png">
</p>

### Step 2: Investigate and prepare your data

To create a data visualization with the Data visualization component in Studio, you need some geospatial data in a Mapbox-hosted vector [tileset](https://docs.mapbox.com/studio-manual/reference/tilesets/#what-is-a-tileset). You could upload data as shapefiles, which would be converted into a tileset. For ease of use, and to focus on data-driven-styling, we will use Mapbox supplied, hosted tilesets below.

**Optional:** If you want to preview these tilesets in the Mapbox Studio [Tileset explorer](https://docs.mapbox.com/studio-manual/reference/tilesets/#tileset-explorer), log into your Mapbox account and click on each dataset to view more information. 

<br>

### **_II. Create a choropleth map_**

To create a **Choropleth** visualization, we can use [data on annual temperature changes for U.S. counties](https://console.mapbox.com/studio/tilesets/mapbox.brt3djy1/#3.44/35.82/-100.67), which contains polygon features.

Open the link to view the data in the Tileset editor. 
   - Notice on the left, there is a list of 14 fields (a.k.a. attributes) for this layer. Click on the map to see information about a given feature.
   - Use the **Share** button on the right to find the Tileset ID which is used to add this data, as map tiles, to a Mapbox Style (via Mapbox Studio or using JS).

<p align="center">
    <img src= "Images\04_WaPoCounties.png">
</p>

This tileset includes county temperature change data from the [The Washington Post's "2ºC: Beyond the Limit" series](https://github.com/washingtonpost/data-2C-beyond-the-limit-usa).  to set the colors of regional polygons:

- Yellow polygons <div style="background-color: #EDF51C; height: 1rem; width: 1rem; border-radius: 4px; display: inline-block; margin: .3rem; margin-bottom: 0;"></div>`#EDF51C` will represent counties with warmer temperatures.
- Purple polygons <div style="background-color: #67009E; height: 1rem; width: 1rem; border-radius: 4px; display: inline-block; margin: .3rem; margin-bottom: 0"></div>`#67009E` will represent counties with cooler temperatures.


### Step 1: Add the Data visualization Component
To add the _Data visualization component_ to your style, follow these steps:

1. Return to your "Blank" style and rename it "County Temp Change" or another name that clearly communicates the topic.
2. Add the tileset as a map component: Add new layer (+) >  Components > Data visualization.
3. Select the data source under **Source**, where it says "None selected", then click the Add source by ID tab.

<p align="center">
    <img src= "Images\04-AddSourceByID.png">
</p>
   
4. Copy the tileset ID: `mapbox.brt3djy1`, paste it into the search box, and click Find.
   You could add your own uploaded, hosted data using this method as well.
6. Click Select data visualization type to continue.
7. Click Select Choropleth to add the component to your style!

The component will select and style a field from the `wapo-county-temp-change-c168xj` tileset automatically when you add it to the map. Zoom to the contiguous United States to get a better sense of the data on your map.

By default, the component will select the field `tempchg` to style _Color_ from the palette `Polar`.

<p align="center">
    <img src= "Images\04-initalTempChange.png">
</p>


### Step 2: Refine your visualization
In this step, you will refine the appearance of your visualization by changing the color palette. The field `tempchg` has values above and below `0`. To make the visualization reflect divergence from `0` with color, the second stop should be `0` instead of the default value of `1.774`.

1. Click the second stop value for Color from its default value of 1.774 to 0.
Next, you will adjust the colors in your visualization by changing the palette selection.
2. Click on the top Choropleth layer in the layers hierarchy on the left side of the screen.
3. In the new tab that appears, click the palette dropdown.
4. Select **Temperate** from the options provided.

For this data, higher values indicate warmer temperatures and lower values indicate colder temperatures.

To make your map reflect the temperature visually, you will need to flip the colors.

5. To flip the colors, click the u-turn arrow button, named **Reverse Palette Order**.
     - The button name will appear when you hover over the button.
6. If you want to experiment with additional styling options for your choropleth map, adjust the following settings in the component controls:
     - To add more stops to your color palette, click **+ Add stop** and enter a value.
     - To show or hide outlines on your polygons, toggle the control for _Stroke_.
     - To show or hide labels on your map, toggle the control for _Labels_.
     - To apply transparency to your polygons, drag the slider for _Opacity_.

**Assignment task:** change at least 2 of these settings (e.g. color palette, number of stops, value of stops), and tell us 1) *what* you changed and 2) provide an explanation for *why* you changed them, based on lecture material or readings. This should be at least 2 sentences per setting.<br>
*Color palette note: sequential color scheme (like the demo) is acceptable, but a divergent scheme will better highlight the positive/negative differences.*


   
Below is an example of how your choropleth visualization could look:

<p align="center">
    <img src= "Images\dataviz_choropleth.png" alt="choropleth map of temperature change in the US" by county>
</p>

### Step 3: Publish your style

When you have finished editing your map style, publish your changes by clicking the **Publish** button in the upper right side of the screen. When you click the publish button, a window will display the difference between the previous and current version of this style. If you're happy with the changes, click **Publish**. 

### Step 4: Add your style to a map

In assignment 1, you made your first map. Using the quickstart code, create a full-page map using this Style.
Remember you'll have to:
1. Click *Share* to get the Style URL for this map
<p align="center">
    <img src= "Images\04-sharestyle.png">
</p>
   
2. In `QuickStartMap.html` (the file used to build the assignment 1 map), add the Mapbox CSS and JS references to the header.
    ```html
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v3.24.0/mapbox-gl.css' rel='stylesheet' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v3.24.0/mapbox-gl.js'></script>
    ```
3. Insert a map div
4. Use JS to initialize the map
   - set the style
   - set the initial center
   - set the initial zoom
5. Add CSS to style the map div
6. Optionally add zoom controls and a title header
7. You do **NOT** need to add markers or popups
8. Add descriptive comments to major codeblocks and clean up your whitespace
<br>

### Step 5: Upload your map to GitHub

Upload your map to GitHub so it can be viewed publicly.


<br>
<br>


**Assignment task:** : Pick **ONE** from the following (Data driven circles or Symbols map)


### **_III. Create a data-driven circles map_**

In this section, we are going to create a data-driven circles visualization using data from the [USGS' Earthquake Hazards Program](https://earthquake.usgs.gov/fdsnws/event/1/). Your data-driven circles map will visualize all reported earthquakes in 2021, using different circle sizes and colors depending on the magnitude of each earthquake.

### Step 1: Explore the data in the tileset editor
- To create a **Data-driven circles** visualization, you can use the tileset [global earthquake data for 2021](https://console.mapbox.com/studio/tilesets/mapbox.5sq1s796/#2.73/44.9/-136.77), which contains point features.

### Step 2: Create a new style
Create a new style and name it accordingly.

### Step 3: Add the Data visualization Component
To add the _Data visualization_ component to your style:

1. In the Components panel, click the plus icon (**+**) and select Data visualization.
2. Select your data source by clicking the Source field, then click the Add source by ID tab.
3. Copy the tileset ID `mapbox.5sq1s796`, paste it into the search box, and click **Find**.
4. Click Select data visualization type to continue.
5. Click Select Data-driven circles to add the component to your style.

The component will select and style a field from the `2021-earthquakes-1vushc` tileset automatically when you add it to the map. Zoom out to see the entire Pacific Ocean to get a better sense of the data on your map.

By default, the component will select the field `dmin` to style **circle size** and a single color from the palette `Polar` for all circles.

### Step 4: Style another data-driven property
In this step, you will use the data in your tileset to control the style of an additional paint property in your style.

By default, all features in data-driven circles are the same color. You will change your visualization to color each circle according to the magnitude of the earthquake it represents.

To make `color` a data-driven property, you will need to add a data field in the _Color_ property.

1. Add `mag` (the value for the magnitude of an earthquake) as the data field for Color.

To adjust the colors in your visualization, you will change the palette selection.

2. In the _Colors_ tab of the _Component_ panel, click the drop-down menu to change the color palette selection. Try _Temperate_ to see how the palette changes the appearance of your visualization.

To emphasize the magnitude of each earthquake on the map, adjust the following component properties to enhance your visualization:

3. To change or add a data field for a data-driven property, select a new data field from the list. This example uses `mag` as the data field for _Size_.
4. To adjust the stop values for _Size_ and _Color_, select the existing values and enter custom values of your choice. This example uses three stops for each: `0.1`, `3`, and `7`.
5. To apply transparency to your circles, drag the slider for _Opacity_. This example shows opacity at `0.2`.
6. To turn off the outlines on your circles, toggle the control for _Stroke_.
7. To adjust the size of all circles on the map together, drag the slider for _Adjust_ sizing. This example shows the sizing slightly above the default setting.

Below is an example of how your data-driven circles visualization should look:

<p align="center">
    <img src= "Images\dataviz_circles.png" alt="map with circles showcasing earthquake locations near Alaska">
</p>

**Assignment task**: change at least 2 settings related to the symbolization, and tell us 1) *what* you changed and 2) provide an explanation for *why* you changed them, based on lecture material or readings. This should be at least 2 sentences per setting.<br>
*Color palette note: Consider the "firefly" guideline on a dark basemap. Typically it's best to assign the light/bright color to the high magnitude values.  Try it out and decide for yourself.*

### Step 5: Publish your style

When you have finished editing your map style, publish your changes by clicking the **Publish** button in the upper right side of the screen. When you click the publish button, a window will display the difference between the previous and current version of this style. If you're happy with the changes, click **Publish**. Your style will now be available to share from a variety of tools and applications.


### Step 6: Add your style to a map

In assignment 1, you made your first map. Using the quickstart code, create a full-page map using this Style.
Remember you'll have to:
1. Click *Share* to get the Style URL for this map
<p align="center">
    <img src= "Images\04-sharestyle.png">
</p>
   
2. In the quickstart HTML, add the Mapbox CSS and JS references to the header
3. Add descriptive comments to major codeblocks and clean up your whitespace
4. Insert a map div
5. Use JS to initialize the map
   - set the style
   - set the initial center
   - set the initial zoom
6. Add CSS to style the map div
7. Optionally add zoom controls
8. You do NOT need to add markers or popups
<br>

### Step 7: Upload your map to GitHub

Upload your map to GitHub so it can be viewed publicly.

### **_IV. Create a symbols map_**

In this section we are going to create a Symbols visualization of mountain summits in Rocky Mountain National Park in Colorado, using unique symbols for each summit depending on which county it is in.


### Step 1: Explore the data in the tileset editor
- To create a **Symbols** visualization, you can use [point data of individual summits](https://console.mapbox.com/studio/tilesets/mapbox.0xjxguyu/#9.95/40.3011/-105.7093) in Rocky Mountain National Park in Colorado.

### Step 2: Create a new style
Create a new style and name it accordingly.

### Step 3: Add the Data visualization Component
You will use data from the freely available `mapbox.0xjxguyu` tileset, which contains point data for summits in this region.

To add the _Data visualization component_ to your style:

1. In the _Components_ panel, click the plus icon (**+**) and select _Data visualization_.
2. Select your data source by clicking the _Source_ field, then click the _Add source by ID_ tab.
3. Copy the tileset ID `mapbox.0xjxguyu`, paste it into the search box, and click **Find**.
4. Click **Select data visualization type** to continue.
5. Click **Select Symbols** to add the component to your style.
6. Copy the location name `Rocky Mountain National Park` and paste it into the geocoder in the top right corner of Studio to navigate to _Rocky Mountain National Park_ in Colorado.
7. Zoom out to `z10` to preview your visualization. To see your current zoom level, check the last three values in your browser URL (`/#{zoom}/{lng}/{lat}`) as you edit your style in Mapbox Studio.


### Step 4: Customize your data-driven values
Now you will choose which field from your data set will control the style of your symbols.

In this tutorial, you will use a unique symbol for each county:

- Summits in `Grand` county will use a `circle-15` icon.
- Summits in `Boulder` county will use a `square-15` icon.
- Summits in `Larimer` county will use a `star-15` icon.
- Summits in `Jackson` county will use a `triangle-15` icon.

<br>

1. In the _Symbols_ component properties panel, set the data field for _Icons_ to `COUNTY_NAM` by clicking on the data field and selecting the new field.

The component’s smart styling algorithm selects a data field and creates a scale with its values from your custom data with up to seven different geometric Maki icons.

2. In the _Symbols_ component properties panel, change the data field for _Labels_ to `FEATURE_NA` by clicking on the data field and selecting the new field.

### Step 3: Refine your visualization
To customize the colors your symbols, the symbols themselves, or other component properties, you can use the component properties panel.

1. To change the color of the default geometric icons, select the _Symbols_ color from the _Colors_ tab of the _Component_ panel and select a new color.
2. To select a different icon for a value, click on the existing icon and select a different option from the popup.
3. To upload a custom icon, drag and drop your icon SVG directly into Studio. Repeat step 17 to add it to the Symbols component.

You can also use the controls on the component properties panel to resize icons, change the label font, adjust the halo color around icons, or allow icons to overlap.

For more fine-tuned control over your symbols visualization, you can [style it as a layer](https://docs.mapbox.com/studio-manual/reference/styles/#style-a-layer) using the _Override_ action.

Below is an example of how your data-driven symbols visualization should look:

<p align="center">
    <img src= "Images\dataviz_symbols.png" alt="map of summits in Rocky Mountain National Park symbolized by county">
</p>

##Assignment task##: Focus on 2 aspects of the symbolization (colors, shapes chosen, etc) and tell us 1) *what* you set and 2) provide an explanation for *why* you set it, based on lecture material or readings. This should be at least 2 sentences per setting.

<br>

### Step 4: Add your style to a map

In assignment 1, you made your first map. Using the quickstart code, create a full-page map using this Style.
Remember you'll have to:
1. Click *Share* to get the Style URL for this map
<p align="center">
    <img src= "Images\04-sharestyle.png">
</p>
   
2. In the quickstart HTML, add the Mapbox CSS and JS references to the header.
3. Insert a map div
4. Use JS to initialize the map
   - set the style
   - set the initial center
   - set the initial zoom
5. Add CSS to style the map div
6. Optionally add zoom controls and a title header
7. You do **NOT** need to add markers or popups
8. Add descriptive comments to major codeblocks and clean up your whitespace
<br>

### Step 5: Upload your map to GitHub

Upload your map to GitHub so it can be viewed publicly.

**Congratulations!** That is it for today's activity. Please proceed to the assignment on canvas for details on what to turn in.
<br>
<br>
### **_Advanced: Try it yourself_**
Mapbox has [tutorials for additional visualization types](https://docs.mapbox.com/help/tutorials/create-a-map-with-data-visualization-component/?step=4) with different data that you can work through:

- To create a **Data-driven lines** visualization, you can use [wind speed data from the Hawaiian islands](https://console.mapbox.com/studio/tilesets/mapbox.6w7f94rz/#8.63/19.7276/-155.8961), which contains line features.

- To create a **3D extrusions** visualization, you can use county population [data and results for recent U.S. presidential elections](https://console.mapbox.com/studio/tilesets/mapbox.hist-pres-election-county/#2.71/35.14/-101.1), which contains polygon features.

- To create a **Heatmap** visualization, you can use [point data of individual street trees](https://console.mapbox.com/studio/tilesets/mapbox.9jkhs7qz/#9.96/40.4466/-79.9849) in Pittsburgh, Pennsylvania.

