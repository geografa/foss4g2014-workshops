# Leaflet and Mapbox JavaScript API Fundamentals


---

# Rafa Gutierrez

- @geografa 
- @mapbox 
- help@mapbox.com

---
# What's covered

- Part I - Setting up your environment
- Part II - Leaflet API
- Part III - Mapbox.js API
- Part IV - 

---
# Setting up your environment
Things you will need for this workshop:

- working laptop
- internet access

Good to haves:
- local web server
- Mapbox account (use code FOSS4GWORKSHOPS)

---
# Setting up your environment

---
# Using crowdcast.io
Real time polls: crowdcast.io 

---
# Leafet API
Leaflet API:

### leafletjs.com/reference.html

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
	// create a map in the "map" div, set the view to a given place and zoom
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
#Map events

- click 
- dblclick
- mousedown
- mouseover 
- layeradd 

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

Methods for converting points to latitude/longitude and back

- latLngToLayerPoint( <LatLng> latlng )
- layerPointToLatLng( <Point> point )	
- containerPointToLayerPoint( <Point> point )
- layerPointToContainerPoint( <Point> point )
- latLngToContainerPoint( <LatLng> latlng )
- containerPointToLatLng( <Point> point )	
- project( <LatLng> latlng, <Number> zoom? )
- unproject( <Point> point, <Number> zoom? )	
- mouseEventToContainerPoint( <MouseEvent> event )
- mouseEventToLayerPoint( <MouseEvent> event )
- mouseEventToLatLng( <MouseEvent> event )	

---

# Zoom/pan options

reset	Boolean	false	If true, the map view will be completely reset (without any animations).
pan	pan options	-	Sets the options for the panning (without the zoom change) if it occurs.
zoom	zoom options	-	Sets the options for the zoom change if it occurs.
animate	Boolean	-	An equivalent of passing animate to both zoom and pan options (see below).

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
# tileLayers


---

# Lists

1. Ordered lists
1. Type `‘1. ’` before your text
1. Your list items will begin with a number

- Unordered lists
- Type `‘-’` or `‘*’` or `‘+’` before your text
- Your list items will begin with a bullet

---

# Code samples

Wrap your code with three backticks and specify the language for automatic syntax highlighting. 

```objectivec 
UIView *someView = [[UIView alloc] init];
NSString *string = @"some string that is fairly long, with many words";
```

We scale the text dynamically so it always looks great. You can also use a single indent to switch to a monospace font. 


---

## If you use text and images together, the image is filtered so the text is always readable.

![](https://i.cloudup.com/LYJ78rgOtL-3000x3000.jpeg)

---

### Take a look at the ‘Working with images’ example presentation for a complete overview of what you can do with images in Deckset.

![right](https://i.cloudup.com/iOAN2nyp5c-3000x3000.jpeg)

---

## Videos can be included too, either as local files or YouTube links.

![autoplay](water.mov)

---

# Speaker notes

Add speaker notes to any slide by adding `‘^’` before your notes. Write as much as you like, all notes will be scaled to fit in the display.

^ This is what speaker notes look like when you are presenting with a external display, or practicing in rehearsal mode.

---

# Rehearsal mode

Choose _Rehearsal Slideshow_ from the _View_ menu to run through your presentation and see how it will work on the day.

---

# Aspect Ratios

Easily swap between _16:9_ and _4:3_ in the _Presentation_ menu to suit whichever projector or screen you are using.

---

# More control with a little HTML

If you really must tweak line breaks, you can use the `<br/>` tag to split any line of text.

---

# Resources

- help@mapbox.com
- https://groups.google.com/forum/#!forum/leaflet-js
- https://github.com/Leaflet/Leaflet
- https://github.com/mapbox/mapbox.js
