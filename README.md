# Geo-Heatmap

# Introduction

Create a heatmap based on specific latitude/longitude points to avoid identifying individuals (when sufficiently zoomed-out).

## Initial Source

https://developers.google.com/maps/documentation/javascript/heatmaplayer

# Setup

## 0. Enable Google API

1. Copy index.html-template to index.html
1. Replace "YOUR_GOOGLE_API_KEY" near the end of the file with a valid/active Google API key

N.B. If you need a key, follow the instructions on the Google site: https://developers.google.com/maps/documentation/javascript/get-api-key

## 1. Gather Input

CSV: `<id>,<street>,<city>,<state>,<zip>`

## 2. Process CSV

Upload the CSV to https://geocoding.geo.census.gov/geocoder/locations/addressbatch?form

## 3. Parse Results

The Census app (step #2) will return an updated CSV file indicating what addresses had/hadn't been converted to lat/long

- Extract the lat/long values
- Clean up the NO_MATCH entries

## 4. Update the HTML File

```     function getPoints() {
        return [
          new google.maps.LatLng(X1,Y1),
          new google.maps.LatLng(X2,Y2),
        ...
        ]
```

Update the index.html file by:

1. Removing all existing `new google.maps.LatLng...` lines in the `getPoints` function (toward the end of the file)
1. Adding a new entry in the array for each lat/long pair (e.g. `new google.maps.LatLng(X1,Y1)`)
1. Save the file

# View

- Load the index.html - either by opening the file in the browser or serving it via an http server

# Resources

## US Census

- https://geocoding.geo.census.gov/geocoder/locations/addressbatch?form = US Census processing tool
- https://www.census.gov/data/developers/data-sets/Geocoding-services.html = US Census Geocoding Services documentation

## Google Heatmap

- https://developers-dot-devsite-v2-prod.appspot.com/maps/documentation/javascript/examples/layer-heatmap = initial app baseline
- https://developers.google.com/maps/gmp-get-started = Google maps starting point
- https://developers.google.com/maps/documentation/javascript/heatmaplayer = additional info
- https://developers.google.com/maps/documentation/javascript/maptypes = Different Google map types (roadmap, satellite, etc.)
