<h2 align="center"> Putting a mapbox map into an HTML template </h2>
<h3 align="center"> Part 1: Creating a map and adding it to a layout </h3>



For this first exercise, we will be adding GeoJSON format points to a map using mapbox GLJS. 
You will then add the map the versatile layout template.


  Here are some additional resources you can explore:
  - [Maki-icons](https://labs.mapbox.com/maki-icons/){:target="_blank"} 

----------

### I. Getting setup


1. Save the following files to your R drive, or local computer:
  - filter-markers.html


  When you open the map, you should have a mapbox-light style centered on Washington DC.
	<p align="center">
	    <img src= "Images/DC.JPG">
	  </p>

----------

### II. Adding the GeoJSON data to the map

1. In the scrip section of `filter-markers.html`, add the GeoSJON data structure in a variable called "places" where it says `// ADD THE DATA HERE`. This just loads data into the variable "places", so you won't see a change in the map.

  ```JavaScript
      // This GeoJSON contains features that include an "icon"
    // property. The value of the "icon" property corresponds
    // to an image in the Mapbox Light style's sprite. (Note:
    // the name of images is the value of the "icon" property
    // + "-15".)
    var places = {
        'type': 'FeatureCollection',
        'features': [
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'theatre'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.038659, 38.931567]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'theatre'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.003168, 38.894651]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'bar'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.090372, 38.881189]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'bicycle'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.052477, 38.943951]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'music'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.031706, 38.914581]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'music'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.020945, 38.878241]
                }
            },
            {
                'type': 'Feature',
                'properties': {
                    'icon': 'music'
                },
                'geometry': {
                    'type': 'Point',
                    'coordinates': [-77.007481, 38.876516]
                }
            }
        ]
    };
```
    
2. Once the map loads, add a GeoJSON source containing place coordinates and the layer using an icon image. This goes inside the ` // Map's On 'load' function`.

  ```JavaScript
        // Add a GeoJSON source containing place coordinates and information.
        map.addSource('places', {
            'type': 'geojson',
            'data': places
        });
        
        // add a new layer using the points
        var layerID = 'points';
            map.addLayer({
                'id': layerID,
                'type': 'symbol',
                'source': 'places',
                'layout': {
                    'icon-image': 'marker-15',
                    'icon-allow-overlap': true
                },
            });
  ```  
  
  The markers should be visible on the map as little black squares.
  
  <p align="center">
	    <img src= "Images/DC-Squaremarkers.JPG">
	  </p>
  
3. We are going to change how the data are added. Instead of adding all the points as a single layer, we will iterate through each record of the data and add a new layer if we find a new value in the symbol field. The symbols are from the Style for this map from the [Maki icons](https://labs.mapbox.com/maki-icons/){:target="_blank"}. To add different icon images, you'd need to create your own style refer to the images as shown in the symbology lab or add imges at runtime using                        
via this (add iamge method)[https://docs.mapbox.com/mapbox-gl-js/example/add-image/]{:target="_blank"}.

  DELETE or comment out
    ```JavaScript         
	var layerID = 'points';
	map.addLayer({
		'id': layerID,
		'type': 'symbol',
		'source': 'places',
		'layout': {
		    'icon-image': 'marker-15',
		    'icon-allow-overlap': true
		},
	 });
    ```
4. Under `// add a new layer using the points` add the following chunk of code

  ```JavaScript
        // add a new layer using the points
        places.features.forEach(function (feature) {
            var symbol = feature.properties['icon'];
            var layerID = 'poi-' + symbol;

            // Add a layer for this symbol type if it hasn't been added already.
            if (!map.getLayer(layerID)) {
                map.addLayer({
                    'id': layerID,
                    'type': 'symbol',
                    'source': 'places',
                    'layout': {
                        // These icons are a part of the Mapbox Light style.
                        'icon-image': symbol + '-15',
                        'icon-allow-overlap': true
                    },
                    'filter': ['==', 'icon', symbol]
                });

	//                // Add checkbox and label elements for the layer.
	//                var input = document.createElement('input');
	//                input.type = 'checkbox';
	//                input.id = layerID;
	//                input.checked = true;
	//                filterGroup.appendChild(input);

	//                var label = document.createElement('label');
	//                label.setAttribute('for', layerID);
	//                label.textContent = symbol;
	//                filterGroup.appendChild(label);

	//                // When the checkbox changes, update the visibility of the layer.
	//                input.addEventListener('change', function (e) {
	//                    map.setLayoutProperty(
	//                        layerID,
	//                        'visibility',
	//                        e.target.checked ? 'visible' : 'none'
	//                    );
	//                });
		    }
		});
	    });
   ``` 
   Notice the symbols on the map correspond to the `icon` field of each record in the geoJSON dataset.
   
5. To add the legend, we add checkbox and label elements for each layer. Uncomment the following code-block:
    ```Javascript
	// Add checkbox and label elements for the layer.
	var input = document.createElement('input');
	input.type = 'checkbox';
	input.id = layerID;
	input.checked = true;
	filterGroup.appendChild(input);

	var label = document.createElement('label');
	label.setAttribute('for', layerID);
	label.textContent = symbol;
	filterGroup.appendChild(label);
    ```
	
6. To add interation to the legend, we add a listener to each intupt checkbox. Uncomment the following code block:
    ```Javascript
	// When the checkbox changes, update the visibility of the layer.
	input.addEventListener('change', function (e) {
	    map.setLayoutProperty(
		layerID,
		'visibility',
		e.target.checked ? 'visible' : 'none'
	    );
	});
    ```
   
Viola!! An interactive map that filters layers by value!
   
<hr>
### III. Adding scale dependency
   
   Find where the map is initialized.
   	- Add a min zoom (you pick what the min zoom sould be).  Here is the table of zoom levels: [https://docs.mapbox.com/help/glossary/zoom-level/](https://docs.mapbox.com/help/glossary/zoom-level/){:target="_blank"}
   	- Prevent users from leaving your this bounding around DC by setting the max bounds, per the code block below. Read about max bounds in the API [https://docs.mapbox.com/mapbox-gl-js/api/map/#map#setmaxbounds](https://docs.mapbox.com/mapbox-gl-js/api/map/#map#setmaxbounds){:target="_blank"}
   	
    ```Javascript
	// Set bounds to Washington, DC
		var bounds = [
		    [-77.26383, 38.73854], // Southwest coordinates
		    [-76.83569, 39.00114] // Northeast coordinates 
		];

		var map = new mapboxgl.Map({
			container: 'map',
			style: 'mapbox://styles/mapbox/light-v10',
			center: [-77.04, 38.907],
			zoom: 11.15,
			maxBounds: bounds // Sets bounds from variable above
		});
    ```

<hr>
### IIV. Add it to the versitile layout 
	Note the lecture code version, added directly into the layout. In this version we will add it as an iFrame.
	
	- Add the map via an iFrame  (read about iframes)
	- Change the title
	- Add some desctiptive text the the panel on the left
	- Add some descriptive text to the paragraph on the right


### IIV. Now let's try somthing else. Let's put the same map in a bootsrap template
	
1. Understanding bootsrap
	Bootstrap is a free front-end framework for faster and easier web development.
	Bootstrap also gives you the ability to easily create responsive designs.
	Bootstrap includes HTML and CSS based design templates for typography, forms, buttons, tables, navigation, modals, image carousels and many other, as well as optional JavaScript plugins.
	![image](https://user-images.githubusercontent.com/29931155/117084542-4ee07100-acfc-11eb-90ca-834ee7616c1f.png)

	
	Go through the following sections of the bootstrap 4 tutorial.
	Read the information provided and click on each of the “Try it yourself!” buttons. 
	Add text here and there to see how it fits in the layout.

	https://www.w3schools.com/bootstrap4/bootstrap_get_started.asp 

	Get Started
	Grid Basic
	Typography
	Colors
	Tables
	Images
	Buttons
	![image](https://user-images.githubusercontent.com/29931155/117084583-6b7ca900-acfc-11eb-853f-19f4850dfbcb.png)

	
2. Download the Basic Template	
	
	- Add the map via an iFrame  (read about iframes)
	- Change the title
	- Add some desctiptive text 

<hr>
That is all for today. Next lab, we'll explore editing fonts in the map and in the website!
