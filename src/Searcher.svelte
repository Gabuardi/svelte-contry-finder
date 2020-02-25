<!----------- LOGIC ---------->
<script>
    let search;
    export let result;

    async function getResult() {
        const response = await fetch(`https://restcountries.eu/rest/v2/name/${search}`);
        const responseFormatted = await response.json();

        if (response.ok) {
            return responseFormatted;
        } else {
            throw new Error(responseFormatted.message);
        }
    }

    function buttonHandler() {
        result = getResult();
    }
</script>

<!----------- STYLE ---------->
<style>
    input {
        background-color: yellow;
    }
</style>

<!----------- TEMPLATE ---------->
<label>
    <input bind:value={search}>
</label>

<button on:click={buttonHandler}>Search</button>
