<script>
	let search;
	let result;

	async function getResult() {
		const response = await fetch(`https://restcountries.eu/rest/v2/name/${search}`);
		const responseFormatted = await response.json();

		if (response.ok) {
			return responseFormatted;
		} else {
			const text = await response.text();
			throw new Error(text);
		}

		// const data = await response.json();
		// console.log(data);
		// result = data;
	}

	function buttonHandler() {
		result = getResult();
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

<button on:click={buttonHandler}>Search</button>


	{#await result}
		<p>Loading...</p>
	{:then value}
		{#if value}
			<p>name: {value.name}</p>
			<p>capital: {value.capital}</p>
			<p>population: {value.population}</p>
		{/if}
	{:catch error}
		<p>AAAAAA</p>
	{/await}

