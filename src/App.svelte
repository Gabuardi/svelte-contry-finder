<script>
	let search;
	let result;

	async function getResult() {
		let response = await fetch(`https://restcountries.eu/rest/v2/name/${search}`);
		const data = await response.json();
		console.log(data);
		result = data;
	}
</script>

<style>
	input {
		background-color: yellow;
	}
</style>

<label>
	<input bind:value={search}>
</label>

<button on:click={getResult}>Search</button>

{#if result!==undefined}

	{#await result}
		<p>Loading...</p>
	{:then value}
		<p>name: {value.name}</p>
		<p>capital: {value.capital}</p>
		<p>population: {value.population}</p>
	{:catch error}
		<p>{error}</p>
	{/await}

{/if}
