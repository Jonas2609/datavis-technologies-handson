<script>
    import Scatterplot from "./Scatterplot.svelte";
    import { onMount } from 'svelte';
    import {json} from 'd3-fetch'

    let countries = null;
    onMount(async () => {
        console.log("onMount started!");
        const data = await json('/data/gapminder.json');
        countries = data.find(d => d.year === "1800").countries;
    });
    console.log("Script finished!")
</script>

{#if countries === null}
    <p>Loading data...</p>
{:else}
    <Scatterplot data={countries} />
    
{/if}
