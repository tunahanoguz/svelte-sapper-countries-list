<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`https://restcountries.eu/rest/v2/all`).then(r => r.json()).then(countries => {
			return { countries };
		});
	}
</script>

<script>
	import CountryCard from "../components/CountryCard.svelte";
	export let countries;
	let countriesTemp = countries;
	let searchText = "";

	function searchCountry(){
		countriesTemp = countries.filter(country => country.name.toLowerCase().includes(searchText.toLowerCase()));
	}
</script>

<style>
	#main {
		width: 100%;
	}

	/*.countries {*/
	/*    width: 100%;*/
	/*}*/

	input {
		width: 100%;
		box-sizing: border-box;
		margin-bottom: 15px;
		padding: 15px;
		border: 1px solid #eeeeee;
		border-radius: 15px;
		outline: none;
		font-size: 16px;
	}
</style>

<svelte:head>
	<title>Countries</title>
</svelte:head>

<div id="main">
	<h1>Countries</h1>

	<input
			placeholder="Search a country..."
			bind:value={searchText}
			on:input={searchCountry}
	/>

	<div class="countries">
		{#each countriesTemp as {name, capital, region, flag} (name)}
			<CountryCard
					name={name}
					capital={capital}
					region={region}
					flag={flag}
			/>
		{/each}
	</div>
</div>
