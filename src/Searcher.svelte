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
    .container {
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    input, button {
        width: 100%;
        height: 50px;
        border: none;
        outline: none;
        transition: all 0.3s;
        text-transform: uppercase;
    }

    input {
        padding: 10px;
    }

    button {
        font-size: 20px;
        background-color: orange;
    }

    input:focus {
        border: solid orange 2px;
    }

    button:hover {
        background-color: #c47200;
    }

    @media (min-width: 765px) {
        .container {
            flex-direction: row;
        }
        label {
            width: 100%;
            margin-right: 20px;
        }
        button {
            width: 20%;
        }
    }
</style>

<!----------- TEMPLATE ---------->
<div class="container">
<label>
    <input placeholder="Search a Country" bind:value={search}>
</label>

<button on:click={buttonHandler}>Search</button>
</div>
