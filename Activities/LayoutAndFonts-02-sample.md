<h2 align="center"> Putting a mapbox map into an HTML template </h2>
<h3 align="center"> Part 2: Changing fonts </h3>



For this scond exercise, we will be:
- adding popups to the map features
- adding a google font to the site
- using CSS to apply the font to various parts of the map and site


  Here are some additional resources you can explore:
  - [Maki-icons](https://labs.mapbox.com/maki-icons/){:target="_blank"} 


----------

### I. Getting setup  


1. 

----------

### II. Adding popups to the map

1. 

----------

### III. Chaging the mouse symbol over points 

1. 

----------

### III. Adding a font to the map

Assume a client has asked you to find a free to use "fun or whimsical" font for this map of sites in Washington D.C. In this

1. Visit https://fonts.google.com/ chose a "fun or whimsical" font, but make sure it is still legiable. 
2. Get the HTML/CSS code by clicking "select this font"
3. Insert the html into the `<head>` of your site.
   e.g. If I picked Martel, I would insert the following codde block. You should pick a differnt font, and you'll be asked to explain your choice for the assignment submission:
   ```javascript
      <!--   Link to google font-->
      <link rel="preconnect" href="https://fonts.gstatic.com">
      <link href="https://fonts.googleapis.com/css2?family=Martel&display=swap" rel="stylesheet">
   ```
4. Set the font for the legend "Filter-group":
   In the `<style>` section at the top, locate the class `.filter-group` and delete or comment out the current font `font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;`. Replace it with the font-family that you selected.
   e.g. If I picked Martel, the class `.filter-group` would looke like this:
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
   
4. Set the font for the popups:
   In the `<style>` section at the top, add a class `.mapboxgl-popup` with the font-family that you selected. Adjust the size of the font if yours feels too big, or too small. If I picked Martel, the new class would looke like this:
   ```css
    .mapboxgl-popup{
        font-family: 'Martel', serif;
        font-size: 150%;
    }   
    ```

