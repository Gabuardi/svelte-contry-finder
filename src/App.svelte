<!----------- LOGIC ---------->
<script>
	import Logo from './Logo.svelte';
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
	.logo {
		margin-bottom: 30px;
	}

    :global(body) {
        padding-top: 50px;
        background-color: #404040;
    }

    .content-wrapper {
        width: 90%;
        margin: auto;
    }

    .country-data-wrapper {
        display: flex;
		flex-direction: column;
    }

	.data-box-list {
		/*width: 800px;*/
	}

    .data-box-container {
        margin-bottom: 10px;
    }

	.map-container {
		width: 100%;
		height: 430px;
	}

	@media (min-width: 765px) {
		.country-data-wrapper {
			flex-direction: row;
		}
		.data-box-list {
			margin-right: 20px;
		}
		.map-container {
			flex: 1;
		}
	}

    @media (min-width: 991px) {
        .content-wrapper {
            width: 80%;
        }
    }

	@media (min-width: 1100px) {
		.content-wrapper {
			width: 60%;
		}
	}
</style>

<!----------- TEMPLATE ---------->
<div class="content-wrapper">

	<div class="logo">
		<Logo/>
	</div>

    <Searcher bind:result={data}/>

    {#await data}
        <p>Loading...</p>
    {:then value}
        {#if value}
            <div class="country-data-wrapper">
                <div class="data-box-list">
                    <div class="data-box-container">
                        <DataBox name="Name" data="{value.name}" icon="{value.flag}"/>
                    </div>
                    <div class="data-box-container">
                        <DataBox name="Capital" data="{value.capital}"/>
                    </div>
                    <div class="data-box-container">
                        <DataBox name="Region" data="{value.region}"/>
                    </div>
                    <div class="data-box-container">
                        <DataBox name="Population" data="{value.population}"/>
                    </div>
                    <div class="data-box-container">
                        <DataBox name="Currency"
                                 data="{value.currencies[0].symbol} [{value.currencies[0].code}] - {value.currencies[0].name}"/>
                    </div>
                </div>
				<div class="map-container">
                	<Map lat="{value.latlng[0]}" lon="{value.latlng[1]}"/>
				</div>
            </div>
        {/if}
    {:catch error}
        <p>{error}</p>
    {/await}
</div>
