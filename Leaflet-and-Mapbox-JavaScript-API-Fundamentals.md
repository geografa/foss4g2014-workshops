# Leaflet and Mapbox JavaScript API *Fun*damentals

![](https://i.cloudup.com/G9pEJXWpow-2000x2000.png)

---

![](http://photos-c.ak.instagram.com/hphotos-ak-xfp1/10251379_523161604472306_1215940481_n.jpg)
# [fit]Rafa Gutierrez

- @geografa 
- @mapbox 
- help@mapbox.com

---

#[fit]Mapbox 

---

![](https://cldup.com/I6mx-iZ3mh.gif)

---

![](http://photos-g.ak.instagram.com/hphotos-ak-xpf1/1389443_189967461190950_1746730200_n.jpg)

# [fit]What's covered

- Part I - Setting up your environment
- Part II - Creating an Interactive Map with the Leaflet API
- Part III - Adding Customized and Interactive Mapbox Maps Mapbox.js API
- Part IV - Wrap Up and Next Steps

---
![](http://photos-g.ak.instagram.com/hphotos-ak-xpf1/1389443_189967461190950_1746730200_n.jpg)

# [fit]Part I - Setting up your environment

Things you will need for this workshop:

- working laptop
- internet access

Good to haves:

- slide to follow along: https://github.com/geografa/foss4g2014-workshops/blob/master/Leaflet-and-Mapbox-JavaScript-API-Fundamentals.md
- local web server
- Mapbox account (use code TRYMAPBOXSTUDIO)

---

# [fit]Real time polls and surveys
[Using crowdcast.io](crowdcast.io/e/foss4g) - crowdcast.io

---
![](http://distilleryimage9.ak.instagram.com/42e63454626711e285b022000a9f15de_7.jpg)
#[fit] Part II

---

![](http://distilleryimage9.ak.instagram.com/42e63454626711e285b022000a9f15de_7.jpg)
# [fit] The Leaflet API

## [leafletjs.com/reference.html](http://leafletjs.com/reference.html)

---

# Goal
Make an interactive map of places. The map will have:

- custom layers
- custom markers
- custom interface
- custom tooltips
- added plugins

---

# [fit] Questions so far?

---

# Creating a basic HTML page

http://jsbin.com/jugoh/62/

	<!DOCTYPE html>
	<html>
	<head>
	<meta charset=utf-8 />
	<title>A Leaflet map!</title>
	<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
	
	// include scripts and css here
	
	</head>
	<body>
	
	//your scripts go here
	
	</body>
	<html>

--- 

# Adding CSS and scripts

Use the hosted version of Leaflet as described at http://leafletjs.com/download.html.

    <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css" />
    
	<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>

---

# Adding styles
Create a basic style that makes the map fit the entire page.

	<style>
		body { margin:0; padding:0; }
		#map { position:absolute; top:0; bottom:0; width:100%; }
	</style>

---

# Add a div container to the body that will contain your map.

	<div id='map'></div>

---

# Initializing a map
```javascript
	<script>
	// create a map in the "map" div
	var map = L.map('map');
	</script>

```
---

# Add a tileLayer to the map element

```javascript
var map = L.map('map');

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    	attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a>contributors'
	}).addTo(map);

map.setView([45.522, -122.6777], 13);
```

---

![](https://cldup.com/dYEdpXINGH-3000x3000.png)

---

# Map Controls

Default
- Zoom buttons
- Attribution

Things we can add:
- Layer switcher
- Scale

---

# Map Property handlers

- dragging		
- scrollWheelZoom
- attributionControl

---

# Map state options
- center
- zoom
- layers
- minZoom
- maxZoom
- maxBounds

---

# Add map options

```javascript
// initialize the map on the "map" div with a given center and zoom
var map = L.map('map', {
    center: [45.522, -122.677],
    zoom: 13
});
```
---

# Review adding a tileLayer

```javascript
// add an OpenStreetMap tile layer
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(map);
```
---

# Adding a different tileLayer

```javascript
L.tileLayer('https://{s}.tiles.mapbox.com/v3/{id}/{z}/{x}/{y}.png', {
			attribution: 'Map data &copy;  ' +
			'<a href="http://openstreetmap.org">OpenStreetMap</a> contributors, ' +
			'<a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' +
			'Imagery © <a href="http://mapbox.com">Mapbox</a>',
			id: 'examples.map-i86knfo3'
		}).addTo(map);
```

---

![](https://cldup.com/OJ43f2UBRm-3000x3000.png)  

---

# Add tileLayer options
```
// add an OpenStreetMap tile layer
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
```
---

# [fit]Layers

---

# Available Map Layers

- Tile layers
- Markers
- Popups
- Vector layers: polylines, polygons, circles, rectangles, circle markers
- GeoJSON layers
- Image overlays
- WMS layers
- Layer groups

---

# Adding markers
```javascript
// add a marker in the given location
// attach some popup content to it and 
// open the popup
var myMarker = L.marker([45.52245801087795, -122.67773866653444]).addTo(map);
```    

---

# Marker options
- icon
- clickable
- draggable
- opacity
- riseOnHover

---

```javascript

var myMarker = L.marker([45.52245801087795, -122.67773866653444], {
	draggable: true
}).addTo(map);

```
---

# [fit]Custom icons

---

```javascript
var myIcon = L.icon({
    iconUrl: 'https://cldup.com/jsXu-OReqo-3000x3000.png',
    iconSize: [50,50],
    iconAnchor: [24,50],
    popupAnchor: [1,-50]
});

L.marker([45.52245801087795, -122.67773866653444], {
		icon: myIcon
	})
	.addTo(map);
```

---
# Chaining methods
```javascript
myMarker
	.bindPopup("Hi. I'm a popup. <br> Customize me.")
    .openPopup();
```
---

# Marker events

- click
- dblclick
- mousedown
- mouseover
- contextmenu
- drag
- move
- popupopen

---

# Popups

```javascript
myMarker.bindPopup('Hi there').openPopup();

var myPopup = L.popup()
    .setLatLng([45.54, -122.65])
    .setContent('<p>Hello world!<br />This is a nice popup.</p>')
    .openOn(map);
```

---

# [fit] Back to the map

---
# Methods for getting map state

- getCenter()	
- getZoom()	
- getBounds()

---

# [fit]Console time

Open your browswer's console to issue commands 

- Chrome - console
- Firefox - Firebug

---
```javascript
map.getCenter();
map.panTo([38.8,-77]);
map.setZoom(3);
map.setView([38.89063199187812,-77.01313018798828],8);
```
---

# Interact with the map

```javascript
map.on('click', function() { alert('Clicked on the map!'); });
```

---

```javascript
map.on('click', function() { 
	alert('Coordinates are: ' + 
	map.getCenter().lat + 
	', ' + 
	map.getCenter().lng); 
});
```
---

#Map events

- click 
- dblclick
- mousedown
- mouseover 
- layeradd 

---

# Available Map Layers

- Tile layers
- Markers
- Popups
- Vector layers: polylines, polygons, circles, rectangles, circle markers
- GeoJSON layers
- Image overlays
- WMS layers
- Layer groups

---

#[fit]polylines, polygons, circles, rectangles, circle markers

```javascript
var latlngs = [[45.52, -122.67], 
[45.53, -122.68]];

var myPolyline = L.polyline(latlngs, {
		color: 'red'
	})
	.addTo(map);

```

---

```javascript
// zoom the map to the polyline
map.fitBounds(myPolyline.getBounds());
```

---

# Methods for Layers and Controls

- addLayer(layer)
- removeLayer(layer)	
- hasLayer(layer)	
- eachLayer(function)
- openPopup(popup)	
- openPopup(html,latlng,popup options)	
- closePopup(popup)	
- addControl(control)	
- removeControl(control)

---

# Remove addTo(map) from myMarker and myPolyline

---

#[fit]LayerGroup

```javascript
var myLayers = L.layerGroup([myMarker])
    .addLayer(myPolyline)
    .addTo(map);
```
---

# Example
```javascript
myLayers.eachLayer(function (layer) {
    layer.bindPopup('Hello')
});
```
---

# [fit]Share methods between layers with FeatureGroup

```javascript
L.featureGroup([myMarker, myPolyline])
    .bindPopup('Hello world!')
    .on('click', function() { 
    	alert('Clicked on a group!'); 
    })
    .addTo(map);
```
---

#[fit]GeoJSON

---

```javascript

var data = {
  "type": "Feature",
  "features": [
    {
      "type": "Feature",
      "properties": {
        "title": "DoubleTree Hotel",
        "address": "1000 NE Multnomah Street, Portland, Oregon, 97232",
        "phone": "+1-503-281-6111",
        "marker-symbol": "lodging",
        "color": "#23344c",
        "radius": 300
      },
      "geometry": {
        "type": "Point",
        "coordinates": [
          -122.65522956848145,
          45.53050807819899
        ]
      }
    }
  ]
};

```

---

```javascript
     
var geoJson = L.geoJson(data, {
    pointToLayer: function(feature, latlng) {
        return L.circleMarker(latlng, {
            radius: feature.properties.radius,
            fillColor: '#bada55',
            fillOpacity: .8
        })
    }
});

```

---

```javascript
var geoJson = L.geoJson(data, {
    pointToLayer: function(feature, latlng) {
        return L.circleMarker(latlng, {
            radius: feature.properties.radius,
            fillColor: '#bada55',
            fillOpacity: .8
        })
    },
    onEachFeature: onEachFeature	
});

function onEachFeature(feature, layer) {
      layer.on({
          click: zoomToFeature
      });
}

```
---

# [fit] Questions?

---

![](http://distilleryimage6.ak.instagram.com/3cef2e0ef27511e2b88d22000a1fd1dd_7.jpg)
# [fit] Part III

---

![](http://distilleryimage5.ak.instagram.com/c45f58d6020211e39a3e22000a1f90ce_7.jpg)
# [fit] Mapbox.js API

---

![](http://distilleryimage5.ak.instagram.com/d31f375c02ce11e3802422000a9e014e_7.jpg)
# [fit]Mapbox.js is a plugin for the Leaflet API

---

# Adding CSS and scripts

Use the hosted version of Mapbox as described at https://www.mapbox.com/mapbox.js/.

    <script src='https://api.tiles.mapbox.com/mapbox.js/v2.0.1/mapbox.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox.js/v2.0.1/mapbox.css' rel='stylesheet' />

---

![](http://distilleryimage11.ak.instagram.com/1ee69cc65dd311e2afd722000a1f98d6_7.jpg)
#[fit] Initializing the map

---

```javascript
// L.mapbox.map(element, id|url|tilejson, options)

var map = L.mapbox.map('map')
    .setView([45.512549810900424,-122.68418669700624],7);

```
---
#[fit] Add a tileLayer to the map

```javascript
var layer = L.mapbox.tileLayer('grafa.a962eabc');

layer.addTo(Map);
```

---

#[fit] gridLayers	

---

#[fit] Add gridLayers to the map

```javascript
// The visible tile layer
L.mapbox.tileLayer('examples.map-8ced9urs')
	.addTo(map);

// Load interactivity data into the map with a gridLayer
var myGridLayer = L.mapbox.gridLayer('examples.map-8ced9urs')
	.addTo(map);

// And use that interactivity to drive a control the user can see.
var myGridControl = L.mapbox.gridControl(myGridLayer)
	.addTo(map);

```

---

#[fit] featureLayers

---

#[fit] featureLayers

```javascript

var myFeatureLayer = L.mapbox.featureLayer(geojson)
    .addTo(map);

// or 
var myFeatureLayer = L.mapbox.featureLayer()
    .addTo(map);

// then
myFeatureLayer.loadURL('my_local_markers.geojson')
	.addTo(map);

// loads markers from the map `examples.map-0l53fhk2` on Mapbox,
// if that map has markers
myFeatureLayer.loadID('examples.map-0l53fhk2');

```

---

```javascript
var featureLayer = L.mapbox.featureLayer()
    .loadURL('things.geojson')
    .addTo(map);
```
---

#[fit]Part IV
![](http://distilleryimage0.ak.instagram.com/232c834a941f11e2a3b222000a9f1696_7.jpg)

---

# [fit]Resources
![](http://distilleryimage0.ak.instagram.com/232c834a941f11e2a3b222000a9f1696_7.jpg)


- help@mapbox.com
- https://groups.google.com/forum/#!forum/leaflet-js
- https://github.com/Leaflet/Leaflet
- https://github.com/mapbox/mapbox.js
