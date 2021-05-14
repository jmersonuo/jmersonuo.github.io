<h2 align="center"> Sound and Alt Text</h2>


For this first exercise, we will be adding sound to marker popups in a Mapbox map
  - in popups using an iframe to share a video via absolute link (on the web)
  - in a pupup to share a sound file via a reletive location (on your computer)
  - adding alt-text descriptions to images
  

  Here are some additional resources you can explore:
  - [W3Schools iframes](https://www.w3schools.com/tags/tag_iframe.asp){:target="_blank"} 
  - [W3Schools image alt attribute](https://www.w3schools.com/tags/att_img_alt.asp){:target="_blank"} 
  - [W3Schools audio tag](https://www.w3schools.com/tags/tag_audio.asp){:target="_blank"} 

----------

### I. Getting setup  

The story map template contains 
  - A story content file (config.js). This JSON-formatted text file includes story copy, location information, and settings to control how the map & story are displayed. This is what the storyteller edits.
  - A map story file (index.html). This HTML file reads information from the content file and dynamically builds out the story and map controls. This is what the reader sees.

1. From the course R Drive (R:\Class_Data\Activity6), `save Sound-in-Mapbox-Popup.zip` your R drive. It contains:
  - QickStartMap-withSound.html
  - The folder Sounds, which contains the file yell-YELLBisonEating150313.mp3 'Source: NPS/Neal Herbert, <a href="https://www.nps.gov/yell/learn/photosmultimedia/sounds-bisoneating.htm">NPS</a>'

2. Review the HTML. Notice it has the standard:
  - `<head> ... </head>` 
  - `<style> ... </style>`   (nested within the head)
  - `<body> ... </body>` 
  - `<script> ... </script>`  (nested within the body

  When you open the map, you should have a mapbox-outdoor style centered on Portland.  
  <p align="center">
    <img src= "Images/6-PorltnadOutdoors.JPG"> 
  </p>

----------

### II. Add 3 markers

Let's start by adding 3 markers. Locate the comment `/***  MARKERS  ***/` then add the code block below. Notice that each marker:
  - was set to the color `darkRed`
  - has a Lng/Lat set
  - then is added to the map with the variable named `map`

  ```javascript
   /***  MARKERS  ***/
      // Marker 1 - Portland
     var marker1 = new mapboxgl.Marker({color:'DarkRed'})
        .setLngLat([-122.6788,45.5212]) // Portland 
        .addTo(map);

        
    // Marker 2 - London 
    var marker2 = new mapboxgl.Marker({color:'DarkRed'})
       .setLngLat([-0.1534307, 51.501223]) // London 
       .addTo(map);

        
    // Marker 3 - Yellowstone
    var marker3 = new mapboxgl.Marker({color:'DarkRed'})
      .setLngLat([-110.74524187568,44.706216445069]) // Yellowstone
      .addTo(map);
    /***  END MARKERS  ***/
  ```

  Zoom way out. You should have a mapbox-outdoor style centered on Portland.  
  <p align="center">
    <img src= "Images/6-PorltnadOutdoors.JPG"> 
  </p>
  
----------

### II. Add popups to each marker

1. First we need to initialize three variables `var popup1`, `var popup2`, and `var popup3`. Each is paired with a text-string that will be used for the .setHTML() value `var popup1_content` etc. In the past, we have set the content right within `.setHTML()`, but since the content is going to get pretty long, using a variable let's us stay more organized.  
  Copy in this code block:

   ```javascript
    /***  POPUPS  ***/
        
    // Popup for marker 1  
    var popup1_content = '<h2>Play the video to listen to Portland</h2><br>';
        
    var popup1 = new mapboxgl.Popup({ minWidth:'300px' })
        .setHTML(popup1_content);
       
    // Popup for marker 2  
    var popup2_content = '<h2>Press play to listen to London in 1928</h2><br>';
        
    var popup2 = new mapboxgl.Popup({ minWidth:'300px' })
        .setHTML(popup2_content);

    
    // Popup for marker 3  
    var popup3_content = '<h2>Press play to listen to a bison eating</h2><br>';   
        
    var popup3 = new mapboxgl.Popup({ minWidth:'300px' })
        .setHTML(popup3_content);

   /***  END POPUPS  ***/ 
   ```  
   The popups aren't linked to the markers yet. So, we need to edit the markers so that each is linked to one of the popups.
  

2. Find where marker one is inialized. and add `.setPopup(popup1)` on a new line between the .setLngLat and .addTo(map). It will look like this:
  ```javascript
   // Marker 1 - Portland
   var marker1 = new mapboxgl.Marker({color:'DarkRed'})    
     .setLngLat([-122.6788,45.5212]) // Portland 
     .setPopup(popup1) 
     .addTo(map);
  ```

3. Add `.setPopup(popup2)` to marker2 on a new line between `setLngLat` and `.addTo(map)`.
4. Add `.setPopup(popup3)` to marker3.
5. Zoom and pan to each marker and check that the popups open.

  <p align="center">
    <img src= "Images/6-3markers-Wpopup.JPG"> 
  </p>

----------

### IV. Embed a YouTube video player in popup 1

To embed a YouTube Video, we can add an iframe to the HTML content of `popup1_content`. We will use `+=` to append more html text to the end of the variable.  
For example:
  ```javascript
  var x = "Hello";
  var y = " World";
  
  x += y;
  ```
 x now equals "Hello World".
 
 Let's try with the popup content:

1. locate the popup for marker 1 and add the iframe emned code from https://www.youtube.com/embed/z1AdmS-LqyA

   ```javascript
    // Popup for marker 1  
    var popup1_content = '<h2>Play the video to listen to Portland</h2><br>';
    popup1_content += '<iframe width="300px" src="https://www.youtube.com/embed/z1AdmS-LqyA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>';
   ```
   
     <p align="center">
    <img src= "Images/6-PortlandPopup.JPG"> 
    </p>




----------

### V. Embed a Soundcloud player in popup 2


1.


----------

### V. Embed a sound file using an html audio player in popup 3


1.


----------

### VI. Add an absolute link to a image to popup3 file


1.


----------

### IV. Add alt text to the image


1.
----------

### IV. Add buttons to jump to each location


1.
----------
