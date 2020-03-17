<script context="module">
    export function preload({ params, query }) {
        return this.fetch(`https://restcountries.eu/rest/v2/name/${params.slug}`).then(r => r.json()).then(country => {
            return { country };
        });
    }
</script>

<script>
    export let country;
</script>

<style>
    .backButton {
        color: #999999;
        padding: 10px 20px;
        border: 1px solid #999999;
        border-radius: 100px;
        text-decoration: none;
    }

    .title {
        font-weight: bold;
    }

    .flag {
        width: 70%;
        height: 60%;
        border-radius: 15px;
    }

    .countryDetail {
        display: flex;
        flex-direction: row;
    }

    .countryDetailColumn {
        flex: 0.5;
    }

    .divider {
        height: 30px;
    }
</style>

<svelte:head>
    <title>{country[0].name}</title>
</svelte:head>

<a role="button" href="/" class="backButton">Back to list</a>

<div class="divider"></div>

{#each country as {name, capital, region, subregion, population, flag, languages, currencies}}
    <h1 class="title">{name}</h1>
    <img src={flag} alt={name} class="flag" />

    <div class="divider"></div>

    <div class="countryDetail">
        <div class="countryDetailColumn">
            <h2>Capital</h2>
            <p>{capital}</p>
        </div>

        <div class="countryDetailColumn">
            <h2>Region</h2>
            <p>{region}</p>
        </div>
    </div>

    <div class="divider"></div>

    <div class="countryDetail">
        <div class="countryDetailColumn">
            <h2>Population</h2>
            <p>{population}</p>
        </div>

        <div class="countryDetailColumn">
            <h2>Subregion</h2>
            <p>{subregion}</p>
        </div>
    </div>

    <div class="divider"></div>

    <div class="countryDetail">
        <div class="countryDetailColumn">
            <h2>Languages</h2>
            {#each languages as language}
                <p>{language.name}</p>
            {/each}
        </div>

        <div class="countryDetailColumn">
            <h2>Currencies</h2>
            {#each currencies as currency}
                <p>{currency.name} ({currency.code})</p>
            {/each}
        </div>
    </div>
{/each}

