# Leaflet #

### What is this repository for? ###

* Choropleth Map Of Bangalore With Traffic Visualization 
* Leaflet 1.2.0
* [Learn Leaflet](http://leafletjs.com/examples.html)

### How do I get set up? ###

This step-by-step guide will quickly get you started on Leaflet basics, including setting up a Leaflet map and making a basic Choropleth map.

* Preparing your page
   Before writing any code for the map, you need to do the following preparation steps on your page:

   1. Include Leaflet CSS file in the head section of your document:

         <link rel="stylesheet" href="https://unpkg.com/leaflet@1.2.0/dist/leaflet.css"
             integrity="sha512-M2wvCLH6DSRazYeZRIm1JnYyh22purTM+FDB5CsyxtQJYeKq83arPe5wgbNmcFXGqiSH2XR8dT/fJISVA1r/zQ=="
             crossorigin=""/>

   2. Include Leaflet JavaScript file after Leaflet’s CSS:

         <!-- Make sure you put this AFTER Leaflet's CSS -->
         <script src="https://unpkg.com/leaflet@1.2.0/dist/leaflet.js"
             integrity="sha512-lInM/apFSqyy1o6s89K4iQUKg6ppXEgsVxT35HbzUupEVRh2Eu9Wdl4tHj7dZO0s1uvplcYGmt3498TtHq+log=="
             crossorigin=""></script>
   
   3. Put a div element with a certain id where you want your map to be:

         <div id="mapid"></div>
 
   4. Make sure the map container has a defined height, for example by setting it in CSS:

         #mapid { height: 600px; }

* Setting up the map

   1. Let’s create a map of the center of Bangalore with pretty Mapbox Streets tiles. First we’ll initialize the map and set its view to our chosen geographical coordinates and a zoom level:

         var map = L.map('map').setView([12.977527, 77.635864], 10)
 
   2. Next we’ll add a tile layer to add to our map, in this case it’s a Mapbox Streets tile layer.

         L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={your access token here}', {
             maxZoom: 18,
             attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, ' + '<a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, ' + 'Imagery © <a href="http://mapbox.com">Mapbox</a>',
             id: 'mapbox.light'
         }).addTo(map);
  
         L.geoJson(statesData).addTo(map);
   
* Now we will make a basic Choropleth Map.

   1. Data Source

       We’ll be creating a choropleth map 15 diffrent areas of Bangalore. As the amount of data is not very big, the most convenient and simple way to store and then display it is GeoJSON.

       Sample GeoJson File Of Bangalore --> https://bitbucket.org/bankamitesh/bangalore_traffic/src/2be3f59ce47ad7dbd40241406d7d1c87d5347bec/web/assets/js/test2.js?at=master

       Each feature of our GeoJSON data (test2.js) will look like this:

            {
                 "type": "Feature",
                 "properties": {
                 "name": "Alabama",
                 "density": 94.65
            },
                 "geometry": ...
                 ...
            }

Including the GeoJSON data a basic Choropleth Map of Bangalore will be created. 


### Example ###

* This sample code with create a basic Leaflet map.

        <html>
            <head>
                <title>Leaflet</title>
                <link rel="stylesheet" href="web/assets/css/leaflet.css" integrity="sha512-wcw6ts8Anuw10Mzh9Ytw4pylW8+NAD4ch3lqm9lzAsTxg0GFeJgoAtxuCLREZSC5lUXdVyo/7yfsqFjQ4S+aKw==" crossorigin=""/>
                <script src="web/assets/js/leaflet.js" integrity="sha512-mNqn2Wg7tSToJhvHcqfzLMU6J4mkOImSPTxVZAdo+lcPlk+GhZmYgACEe0x35K7YzW1zJ7XyJV/TT1MrdXvMcA==" crossorigin=""></script>
            <style> 
                #mapid { height: 100%; } 
            </style>
            </head>
            <body>
                <h1>Leaflet Map</h1>
                <div id="mapid"></div>
                <script>
                    var mymap = L.map('mapid').setView([12.977527, 77.635864], 13);
                    L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={accessToken}', {
                        attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://mapbox.com">Mapbox</a>',
                        maxZoom: 18,
                        id: 'mapbox.streets',
                        accessToken: 'pk.eyJ1IjoiYmFua2FtaXRlc2giLCJhIjoiY2o1eG5wOXdsMDdiZzJ3cXNsNjRiaHZoMSJ9.y78IAh9Yi39impJdqoODhQ'
                    }).addTo(mymap);
                </script>
            </body>
        </html> 
 
### Who do I talk to? ###

* Mitesh Banka
    banka.mitesh@gmail.com
    +91-8482096370