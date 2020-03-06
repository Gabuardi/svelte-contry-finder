<!----------- LOGIC ---------->
<script>
import { onMount } from 'svelte'
import mapbox from 'mapbox-gl';

export let lon;
export let lat;

mapbox.accessToken = 'pk.eyJ1IjoiZ2FidWFyZGkiLCJhIjoiY2s3N3o3Mm93MGRjODNtdGZzOHh3ZThxbCJ9.5iVOCSZWjQp0CUWkIVN1Tw';

onMount(() => {
    const link = document.createElement('link');
    link.rel = 'stylesheet';
    link.href = 'https://unpkg.com/mapbox-gl/dist/mapbox-gl.css';

    link.onload = () => {
        new mapbox.Map({
            container: 'map-container',
            style: 'mapbox://styles/mapbox/streets-v9',
            center: [lon, lat],
            zoom: 3
        });
    };

    document.head.appendChild(link);
});
</script>

<style>
    div {
        width: 100%;
        height: 100%;
        border: 2px solid orange;
    }
</style>

<!----------- TEMPLATE ---------->
<div id="map-container"></div>


