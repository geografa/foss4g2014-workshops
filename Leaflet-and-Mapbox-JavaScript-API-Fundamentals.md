# Leaflet and Mapbox JavaScript API Fundamentals

![](https://i.cloudup.com/G9pEJXWpow-2000x2000.png)

---

# Rafa Gutierrez

- @geografa 
- @mapbox 
- help@mapbox.com

---

# What's covered

- Part I - Setting up your environment
- Part II - Creating an Interactive Map with the Leaflet API
- Part III - Adding Customized and Interactive Mapbox Maps Mapbox.js API
- Part IV - Wrap Up and Next Steps

---

# Part I - Setting up your environment

Things you will need for this workshop:

- working laptop
- internet access

Good to haves:

- local web server
- Mapbox account (use code FOSS4GWORKSHOPS)

---

# [fit]Real time polls and surveys
[Using crowdcast.io](http://crowdcast.io/) - crowdcast.io

---

# Part II - Creating an Interactive Map with the Leaflet API

## [Leaflet API](http://leafletjs.com/reference.html) - leafletjs.com/reference.html

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

var myMarker = L.marker([45.52245801087795, -122.67773866653444], {
	draggable: true
}).addTo(map);

---

# [fit]icons

---

var myIcon = L.icon({
    iconUrl: 'https://cldup.com/jsXu-OReqo-3000x3000.png',
    iconSize: [50,50],
    iconAnchor: [24,50],
    popupAnchor: [1,-50]
});

L.marker([45.52245801087795, -122.67773866653444], {icon: myIcon}).addTo(map);

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


---

# Resources

- help@mapbox.com
- https://groups.google.com/forum/#!forum/leaflet-js
- https://github.com/Leaflet/Leaflet
- https://github.com/mapbox/mapbox.js
