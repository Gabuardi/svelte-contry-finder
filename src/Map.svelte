<!----------- LOGIC ---------->
<script>
import { onMount } from 'svelte'
import mapbox from 'mapbox-gl';
mapbox.accessToken = 'pk.eyJ1IjoiZ2FidWFyZGkiLCJhIjoiY2s3N3o3Mm93MGRjODNtdGZzOHh3ZThxbCJ9.5iVOCSZWjQp0CUWkIVN1Tw';

onMount(() => {
    const link = document.createElement('link');
    link.rel = 'stylesheet';
    link.href = 'https://unpkg.com/mapbox-gl/dist/mapbox-gl.css';

    link.onload = () => {
        new mapbox.Map({
            container: 'map-container',
            style: 'mapbox://styles/mapbox/streets-v9',
            center: [-84, 10],
            zoom: 3
        });
    };

    document.head.appendChild(link);
});
</script>

<style>
    div {
        width: 400px;
        height: 400px;
    }
</style>

<!----------- TEMPLATE ---------->
<div id="map-container">
</div>


