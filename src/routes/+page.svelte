<script>
	import { onMount } from 'svelte';
	let platform;
	var mapElement;
	var hereMap;
	onMount(async () => {
		// @ts-ignore
		var H = window.H

		// @ts-ignore
		var platform = new H.service.Platform({
			apikey: 'Zq0QbZGKiWBcdNsm5bgluVcs2vWxsPqaD2vv96W76sk'
		});
		// @ts-ignore
		var defaultLayers = platform.createDefaultLayers();
		// @ts-ignore
		hereMap = new H.Map(mapElement, defaultLayers.vector.normal.map, {
			center: {
				lat: 50,
				lng: 5
			},
			zoom: 4,
			pixelRatio: window.devicePixelRatio || 1
		});
		var behavior = new H.mapevents.Behavior(new H.mapevents.MapEvents(hereMap));
		// @ts-ignore
		var ui = H.ui.UI.createDefault(hereMap, defaultLayers);
	});
</script>

<h1>Welcome to SvelteKit</h1>
<div id="map" bind:this={mapElement} />

<style>
	#map {
		width: 95%;
		height: 800px;
		background: grey;
	}
</style>
