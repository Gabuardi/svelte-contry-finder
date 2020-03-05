<!----------- LOGIC ---------->
<script>
	import Searcher from './Searcher.svelte';
	import Note from './Note.svelte'
	import DataBox from './DataBox.svelte';
	import Map from './Map.svelte';

	let data;

	function parseCountryData(data) {
		return {
			name: data.name,
			capital: data.capital,
			region: data.region,
			population: data.region,
			currency: `${data.currencies[0].symbol} [${data.currencies[0].code}]`
		}
	}
</script>

<!----------- STYLE ---------->
<style>
	:global(body) {
		padding-top: 50px;
		background-color: #404040;
	}

	.searcher {
		width: 90%;
		margin: auto;
	}

	@media (min-width: 765px) {
		.searcher {
			width: 80%;
		}
	}
</style>

<!----------- TEMPLATE ---------->
<div class="searcher">
	<Searcher bind:result={data}/>
</div>


{#await data}
	<p>Loading...</p>
{:then value}
	{#if value}
		<DataBox name="Name" data="{value.name}"/>
		<DataBox name="Capital" data="{value.capital}"/>
		<DataBox name="Region" data="{value.region}"/>
		<DataBox name="Population" data="{value.population}"/>
		<DataBox name="Currency" data="{value.currencies[0].symbol} [{value.currencies[0].code}]"/>
	{/if}
{:catch error}
	<p>{error}</p>
{/await}

<Map/>

<Note>
	<p><strong>Country Finder</strong> shows only the first result found</p>
</Note>
