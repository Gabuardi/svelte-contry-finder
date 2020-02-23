<script>
	let search;
	let result;

	async function getResult() {
		let response = await fetch(`https://restcountries.eu/rest/v2/alpha/${search}`);
    return await response.json();
	}

	function submitHandler() {
		result = getResult();
	}

	let name = 'world';
</script>

<input on:keyup={submitHandler} bind:value={search}>

{#if result!==undefined}

{#await result}
	<p>Loading...</p>
{:then value}
	<p>name: {value.name}</p>
	<p>capital: {value.capital}</p>
	<p>population: {value.population}</p>
	<p>currencies symbol: {value.currencies[0].symbol}</p>
{:catch error}
	<p>{error}</p>
{/await}

{/if}
