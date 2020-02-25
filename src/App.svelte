<script>
	import Searcher from './Searcher.svelte';

	let data;
</script>


<Searcher bind:result={data}/>

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

