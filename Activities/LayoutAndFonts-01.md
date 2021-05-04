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

### II. Adding the GEOJSON DATA

1. In the scrip section, add the data below.

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
