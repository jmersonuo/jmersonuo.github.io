<h2 align="center"> Putting a mapbox map into an HTML template </h2>
<h3 align="center"> Part 1: Creating a map and adding it to a layout </h3>



For this first exercise, we will be adding GeoJSON format points to a map using mapbox GLJS. 
You will then add the map the versitile layout template.


  Here are some additional resources you can explore:
  - [](){:target="_blank"} 

----------

### I. Getting setup


1. Save the following files to your R drive, or local computer:
  - 

----------

### II. Adding the GeoJSON DATA

1. In the scrip section of `filter-markers.html`, add the GeoSJON data structure in a variable called "places" where it says `// ADD THE DATA HERE`.

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
    
2. Once the map loads, // Add a GeoJSON source containing place coordinates and information.

  ```JavaScript
          // Add a GeoJSON source containing place coordinates and information.
        map.addSource('places', {
            'type': 'geojson',
            'data': places
        });
  ```  
3.

  ```JavaScript
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
                        // To view all images available in a Mapbox style, open
                        // the style in Mapbox Studio and click the "Images" tab.
                        // To add a new image to the style at runtime see
                        // https://docs.mapbox.com/mapbox-gl-js/example/add-image/
                        'icon-image': symbol + '-15',
                        'icon-allow-overlap': true
                    },
                    'filter': ['==', 'icon', symbol]
                });

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

                // When the checkbox changes, update the visibility of the layer.
                input.addEventListener('change', function (e) {
                    map.setLayoutProperty(
                        layerID,
                        'visibility',
                        e.target.checked ? 'visible' : 'none'
                    );
                });
            }
        });
   ``` 
