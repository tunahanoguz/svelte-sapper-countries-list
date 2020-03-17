<script>
    export let name, capital, region, flag;
</script>

<style>
    #country {
        display: flex;
        flex-direction: row;
        align-items: center;
        align-self: center;
        margin-bottom: 10px;
        padding: 15px;
        background-color: #eeeeee;
        border-radius: 15px;
    }

    .flag {
        width: 50px;
        height: 50px;
        margin-right: 20px;
        border-radius: 15px;
    }

    .countryDetails {
        flex: 1;
    }

    .countryName {
        margin: 0;
        padding: 0;
        font-size: 18px;
        font-weight: bold;
    }

    a {
        text-decoration: none;
    }
</style>

<a id="country" href="/country/{name}">
    <img src={flag} class="flag"/>
    <div class="countryDetails">
        <h1 class="countryName">{name}</h1>
    </div>
</a>
