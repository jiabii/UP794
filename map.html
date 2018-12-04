<!DOCTYPE html>
<html>

<head>
	<title>WindMap with Leaflet</title>

	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">

	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.4/dist/leaflet.css"
   integrity="sha512-puBpdR0798OZvTTbP4A8Ix/l+A4dHDD0DGqYW6RQ+9jxkRFclaxxQb/SJAWZfWAkuyeQUytO7+7N4QKrDh+drA=="
   crossorigin=""/>
	<link rel="stylesheet" href="map.css" />
</head>

<body>
	<div id="container"></div>

	<script src="https://unpkg.com/leaflet@1.3.4/dist/leaflet.js"
   integrity="sha512-nMMmRyTVoLYqjP9hrbed9S+FzjZHW5gY1TWCHA5ckwXZBadntCNs8kEqAWdrb9O7rxbCaA4lKTIWjDXZxflOcA=="
   crossorigin=""></script>
	<script src="L.CanvasLayer.js"></script>
	<script src="windy.js"></script>
	<script>
		var WINDY, CANVAS;
		var mapBase;
		var windMapLayer;

		window.onload = function() {
	
			if (!document.createElement("canvas").getContext)
				return alert("This browser doesn't support canvas");

			mapBase = L.map("container").setView([45, -90], 5);

			L.tileLayer("http://{s}.tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png", {
				attribution: "Map data © <a href='https://www.openstreetmap.org'>OpenStreetMap</a> contributors, CC-BY-SA"
			}).addTo(mapBase);

			windMapLayer = L.canvasLayer();
			windMapLayer.delegate(this).addTo(mapBase);

			mapBase.on("moveend", function() {
				
				redrawWind();
			});
			

		}

		function onDrawLayer(source) {
			fetch("gfs.json")
				.then(function(response) {
					if (!response.ok) {
						console.log("gfs.json access. Status code: " + response.status);
						return;
					}
					return response.json();
				})
				.then(function(json) {
					var gfsdata = json;

					CANVAS = source.canvas;

					CANVAS.id = "WindMapLayer";
					CANVAS.width = document.getElementById("container").offsetWidth;
					CANVAS.height = document.getElementById("container").offsetHeight;
					CANVAS.style.zIndex = 99;
					CANVAS.style.position = "absolute";

					WINDY = new Windy({
						canvas: CANVAS,
						data: gfsdata
					});

					redrawWind();
				})
				.catch(function(error) {
					console.log(" There was an error parsing.", error)
				})
		}

		function redrawWind() {
			WINDY.stop();

			var bnds = mapBase.getBounds();
			var z = mapBase.getZoom();
			var width = document.getElementById("container").offsetWidth;
			var height = document.getElementById("container").offsetHeight;

			CANVAS.width = width;
			CANVAS.height = height;

			VELOCITY_SCALE = 1 / (3400 * z * z); // scale for wind velocity (completely arbitrary--this value looks nice)
			PARTICLE_LINE_WIDTH = 0.1 * z + 0.267; // line width of a drawn particle
			PARTICLE_MULTIPLIER = 32 * Math.pow(z, -1.28); // particle count scalar (completely arbitrary--container)
			PARTICLE_REDUCTION = 11.5 * Math.pow(z, -1.5); // reduce particle count to this much of normal for mobile devices
			MAX_WIND_INTENSITY = 40; // wind velocity at which particle intensity is maximum (m/s)
			MAX_PARTICLE_AGE = 20; // max number of frames a particle is drawn before regeneration

			WINDY.start(
				[
					[0, 0],
					[width, height]
				],
				width,
				height, [
					[bnds.getWest(), bnds.getSouth()],
					[bnds.getEast(), bnds.getNorth()]
				]
			);
		}

	</script>
	
</body>

</html>
