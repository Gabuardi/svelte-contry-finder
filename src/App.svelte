<!----------- LOGIC ---------->
<script>
	import Searcher from './Searcher.svelte';

	let data;
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
		<p>name: {value.name}</p>
		<p>capital: {value.capital}</p>
		<p>population: {value.population}</p>
	{/if}
{:catch error}
	<p>{error}</p>
{/await}

