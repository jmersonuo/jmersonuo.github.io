<h2 align="center"> Putting a mapbox map into an HTML template </h2>
<h3 align="center"> Part 2: Changing fonts and getting a little more advanced with looping through data</h3>



For this second exercise, we will be:
- adding popups to the map features
- adding a google font to the site
- using CSS to apply the font to various parts of the map and site


----------

### I. Getting setup  


1. Open the HTML files that you started eding in part 1.

----------

### II. Adding popups to the map

In order to add popups we need to specify the popup function for each of the layers.  We will do this within the forEach function that looks at each record in the geoJSON (` places.features.forEach(function (feature) {... }`), and within the if condition that checks the map or new icon types (`if (!map.getLayer(layerID)) {... }`).  

1. *Locate* the last line of within the scope of (`if (!map.getLayer(layerID)) {... }`).  It should be the checkbox's change function:
   ```javascript
     // When the checkbox changes, update the visibility of the layer.
     input.addEventListener('change', function (e) {
           map.setLayoutProperty(
               layerID,
               'visibility',
               e.target.checked ? 'visible' : 'none'
           );
      });
   ```
    
2. After this, add the following code block that will create variable that builds an HTML description for each point, gets the coordinates of each point, and then uses that description for the HTML of the popup that will open at the point's coordinates. Because this is within the same loop, so it is added for each layer using the variable `layerID`. In past assignments, we had explicitly named the layer for `map.on` functions.

   ```javascript
     // When a click event occurs on a feature in the places layer, 
     // open a popup at the location of the feature, with description HTML from its properties.
     map.on('click', layerID, function (e) {
            var coordinates = e.features[0].geometry.coordinates.slice();
            var description = "This is a map point <br> Type: " + e.features[0].properties.icon;

            new mapboxgl.Popup()
            .setLngLat(coordinates)
            .setHTML(description)
            .addTo(map);
     });
   ```  
3. Try clicking on a map point, a popup should open!
   <p align="center">
	    <img src= "Images/05-popup.JPG"> 
   </p>
 
  
4. For an extra challenge, edit the value of the `description` variable to modify the text within the popup.

----------

### III. Changing the mouse symbol over points 

Thinking about accordance, we should let our users know that the points are clickable. To do so, lets change the mouse cursor to a pointer when we roll over a feature in each layer. Just like the previous step, this is within a loop, so it is added for each layer using the variable `layerID`. In past assignments, we had explicitly named the layer for `map.on` functions.

1. In the same scope as the code above (`if (!map.getLayer(layerID)) {...}`), right after the code block for the popups, add the following code block:
  ```javascript
     // Change the cursor to a pointer when the mouse is over the places layer.
     map.on('mouseenter', layerID, function () {
          map.getCanvas().style.cursor = 'pointer';
     });

     // Change it back to a pointer when it leaves.
     map.on('mouseleave', layerID, function () {
            map.getCanvas().style.cursor = '';
     });
  ```

2. Hover over points in the map. Does your mouse chnage? Yes? hurrah!

----------

### IV. Adding a font to the map

Assume a client has asked you to find a free to use "fun or whimsical" font for this map of sites in Washington D.C. In this

1. Visit https://fonts.google.com/ chose a "fun or whimsical" font, but make sure it is still legible. 
2. Get the HTML/CSS code by clicking "select this font"
3. Insert the html into the `<head>` of your site.
   e.g. If I picked Martel, I would insert the following code block. You should pick a different font, and you'll be asked to explain your choice for the assignment submission:
   ```html
      <!--   Link to google font-->
      <link rel="preconnect" href="https://fonts.gstatic.com">
      <link href="https://fonts.googleapis.com/css2?family=Martel&display=swap" rel="stylesheet">
   ```
4. Set the font for the legend "Filter-group":
   In the `<style>` section, *locate* the existing class `.filter-group` and delete or comment out the current font `font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;`. Replace it with the font-family that you selected.
   e.g. If I picked Martel, the class `.filter-group` would look like this:
   ```css
   .filter-group {
        font-family: 'Martel', serif;
        font-weight: 600;
        position: absolute;
        top: 10px;
        right: 10px;
        z-index: 1;
        border-radius: 3px;
        width: 120px;
        color: #fff;
    }
   ```
   
5. Set the font for the popups:
   In the `<style>` section in the , add a class `.mapboxgl-popup` with the font-family that you selected. Adjust the size of the font if yours feels too big, or too small. If I picked Martel, the new class would look like this:
   ```css
    .mapboxgl-popup{
        font-family: 'Martel', serif;
        font-size: 150%;
    }   
    ```

Here is an example with Martel. Yours should use a different font.
   <p align="center">
	    <img src= "Images/05-popup-font.JPG">
   </p>

----------

### V. Adding a font to the parent webpage (versatile layout)

So far, the edits we made make changes to the map. Since the map is in an iFrame in another web page, we edit it separately.

1. Open your file `VersitileLayout.html`, or whatever you named the html file that has an iframe containing your map.
2. In the `<head>`, add a link to your google font. e.g. for Martel, it looks like this:
   ```html
      <!--   Link to google font-->
      <link rel="preconnect" href="https://fonts.gstatic.com">
      <link href="https://fonts.googleapis.com/css2?family=Martel&display=swap" rel="stylesheet">
   ```
3. *Notice* that the `<head>` contains a relative link to a CSS file, rather than embedding it directly in the HTML file: 
   ```html
     <link href="VersitileLayout.css" rel="stylesheet" />
   ```
4. Open the `VersitileLayout.css` with your text editor. There are a lot of classes already defined for us, but thankfully they are well commented! 
5. *Locate* the class `.site-title` and add your font-family:
   ```css
   .site-title {
	  font-size: 1.25rem;
	  line-height: $site-header-height;
	  font-family: 'Martel', serif;  /* google font was added here */
   }
   ```
6.  *Locate* the class `.site-main` and add your font-family:
   ```css
   .site-main {
	  font-family: 'Martel', serif;  /* google font was added here */
	  position: relative;
	  z-index: 1;
   ```


----------
### VI. Cleaning things up a bit

Often, templates have sections that we aren't going to use, so we can remove them.  Currently, we are not using the search bar. So let's hide it. To do so, we can simply remove the DOM elements from the HTML by commenting them out, we could delete them later if we are sure we don't want them.

1. *locate* the search container, it looks like this. Use an HTML block comment `<!--` to `-->` to comment it out.
  ```html
	<!--
	<div class="search-container cell medium-3 large-2">
	    <input type="text" placeholder="Search..." class="search" />
	    <ul class="search-results no-bullet">
		<li>Search Result 1</li>
		<li>Search Result 2</li>
		<li>Search Result 3</li>
	    </ul>
	</div>
	-->
   ```
   
 2. Customize the layout by editing the CSS so that the header matches the legend box. I am going edit the `.site-header` class to have the same color text as the map menu. You change change both to different colors.
  - In `filter-markers.html`, the CSS at the top has a class `.filter-group` 
  
   ```css
    .filter-group input[type='checkbox'] + label {
        background-color: #3386c0;
        text-transform: capitalize;
    }
   ```
   
  - In `VersitileLayout.css`, the we can change the `.site-title` color.
  
   ```css
    .site-title {
	  color: #3386c0;
	  font-size: 1.25rem;
	  line-height: $site-header-height;
	  font-family: 'Martel', serif;  /* google font was added here */
    }
   ```
   
 ### We've begun to customize the layout!  
  <p align="center">
	    <img src= "Images/05-Header-title.JPG"> 
     </p>
     
### What to turn in:
- Upload your layout to Pages by uploading the map's html, and the layout's html, js, and css files. 
- Visit the site yourself to make sure it works! Don't forget, on Pages, filenames are case sensitive! So the file names need to match the references within the html file EXACTLY!
- Use the submission link to provide the link to your *layout*, attached the same files, and answer the questions listed.
