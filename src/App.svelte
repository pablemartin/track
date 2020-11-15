<script>
	export let name;
	import { onMount } from 'svelte';
	import {LeafletMap, Marker, TileLayer} from 'svelte-leafletjs';

	onMount(() => {
		if (navigator.geolocation){
			navigator.geolocation.getCurrentPosition(position => {
			  console.log(position.coords)
			})
		}
	})

	const mapOptions = {
			center: [1.364917, 103.822872],
			zoom: 11,
	};
	const tileUrl = "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png";
	const tileLayerOptions = {
			minZoom: 0,
			maxZoom: 20,
			maxNativeZoom: 19,
			attribution: "© OpenStreetMap contributors",
	};

	let leafletMap;
</script>

<main>
	<LeafletMap bind:this={leafletMap} options={mapOptions}>
      <TileLayer url={tileUrl} options={tileLayerOptions}/>
			<Marker latLng={[1.282375, 103.864273]}/>
  </LeafletMap>
</main>

<style>
	main {
		text-align: center;
		/* padding: 1em; */
		width: 100%;
		height: 100%;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
