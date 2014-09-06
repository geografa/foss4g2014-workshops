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

	<script>
	// create a map in the "map" div
	var map = L.map('map');

---

# Add a tileLayer to the map element

```javascript
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

```javascript
// initialize the map on the "map" div with a given center and zoom
var map = L.map('map', {
    center: [51.505, -0.09],
    zoom: 13
});
```
---

# Adding a tileLayer

```javascript
// add an OpenStreetMap tile layer
L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png').addTo(map);
```
---

![left](https://i.cloudup.com/LYJ78rgOtL-3000x3000.jpeg)  

now we have a map

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

![](map.getZoom.gif)

---

#Map events

- click 
- dblclick
- mousedown
- mouseover 
- layeradd 

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
```javascript
// add a marker in the given location
// attach some popup content to it and 
// open the popup
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
```javascript
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

```javascript
L.marker([45.522, -122.677]).addTo(map);
```
---
# Marker options
- icon
- clickable
- draggable
- opacity
- riseOnHover

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
marker.bindPopup(popupContent).openPopup();
```
	
---
# Resources

- help@mapbox.com
- https://groups.google.com/forum/#!forum/leaflet-js
- https://github.com/Leaflet/Leaflet
- https://github.com/mapbox/mapbox.js
