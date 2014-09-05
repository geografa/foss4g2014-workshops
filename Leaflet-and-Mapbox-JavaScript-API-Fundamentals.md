# Leaflet and Mapbox JavaScript API Fundamentals


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
# Setting up your environment
Things you will need for this workshop:
- working laptop
- internet access

Good to haves:
- local web server
- Mapbox account (use code FOSS4GWORKSHOPS)

---
# Using crowdcast.io
Real time polls and surveys: [crowdcast.io](http://crowdcast.io/) 

---
# Part II - Creating an Interactive Map with the Leaflet API

## [Leaflet API](http://leafletjs.com/reference.html) - leafletjs.com/reference.html

---
# Goal
Make an interactive map of places. The map will have:
- custom layers
- layer controls
- custom interface
- custom tooltips
- added plugins

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

    <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.css" />
    
	<script src="http://cdn.leafletjs.com/leaflet-0.7.3/leaflet.js"></script>

---
# Adding styles
	<style>
		body { margin:0; padding:0; }
		#map { position:absolute; top:0; bottom:0; width:100%; }
	</style>

---

# Add the div to the body

	<div id='map'></div>

---

# Initializing a map

	<script>
	// create a map in the "map" div
	var map = L.map('map');

---
# Add a tileLayer to the map element

```
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    	attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a>contributors'
	}).addTo(map);
```

---
# Map Controls

- Zoom buttons
- Attribution
- Layer switcher
- Scale

---
# Map state options
- center
- zoom
- layers
- minZoom
- maxZoom
- maxBounds
- crs

---
# Add map options

```
// initialize the map on the "map" div with a given center and zoom
var map = L.map('map', {
    center: [51.505, -0.09],
    zoom: 13
});
```
---
# Methods for modifying map state

- setView( <LatLng> center, <Number> zoom?, <zoom/pan options> options? )
- setZoom( <Number> zoom, <zoom options> options? )
- fitBounds( <LatLngBounds> bounds, <fitBounds options> options? )
- panTo( <LatLng> latlng, <pan options> options? )
- panBy( <Point> point, <pan options> options? )
- setMaxBounds( <LatLngBounds> bounds
- remove()

---
# Console time!
Bust out the console.

---
#Map events

- click 
- dblclick
- mousedown
- mouseover 
- layeradd 

---
# Adding a tileLayer
```
// add an OpenStreetMap tile layer
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(map);
```
---
# Add tileLayer options
```
// add an OpenStreetMap tile layer
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
```
---
# Adding markers
```
// add a marker in the given location, attach some popup content to it and open the popup
L.marker([51.5, -0.09]).addTo(map)
    .bindPopup('A pretty CSS3 popup. <br> Easily customizable.')
    .openPopup();
```    
---
# Methods for getting map state

- getCenter()	
- getZoom()	
- getBounds()


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
# Example
```
map.eachLayer(function (layer) {
    layer.bindPopup('Hello');
});
```
---
# Conversion methods

## Methods for converting points to latitude/longitude and back

- latLngToLayerPoint( <LatLng> latlng )
- layerPointToLatLng( <Point> point )	

---

# Zoom/pan options
- reset
- pan
- zoom
- animate

---
# Other options
- Locate
- Pan
- Zoom
- fit Bounds

---
# Property handlers

- dragging	
- touchZoom	
- doubleClickZoom	
- scrollWheelZoom	
- boxZoom	
- keyboard	
- tap	
- zoomControl
- attributionControl

---
# Markers
L.marker([45.522, -122.677]).addTo(map);

---
# Marker options
- icon
- clickable
- draggable
- keyboard
- title
- alt
- zIndexOffset
- opacity
- riseOnHover
- riseOffset

---
# Marker events

- click
- dblclick
- mousedown
- mouseover
- mouseout
- contextmenu
- dragstart
- drag
- dragend
- move
- add
- remove
- popupopen
- popupclose

---
# Popups
Popups

```
marker.bindPopup(popupContent).openPopup();

```
	
---
# Resources

- help@mapbox.com
- https://groups.google.com/forum/#!forum/leaflet-js
- https://github.com/Leaflet/Leaflet
- https://github.com/mapbox/mapbox.js
