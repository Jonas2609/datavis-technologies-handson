<script>
  import { json } from "d3-fetch";
  import { onMount } from "svelte";

  import Controls from "./Controls.svelte";
  import Scatterplot from "./Scatterplot.svelte";

   // Define a variable to store the filtered countries
   let filteredCountries = [];
   let selectedContinent = null;
   let selectedYear = 0;
  // Load the data
  let data = null;
  onMount(async () => {
    data = await json("/data/gapminder.json");
    filteredCountries = data[0]['countries'];
    
  });  
  // const continent = ["europe", "asia", "americas", "africa"];  // Function to filter countries by continent

   const filterByContinentAndYear = (continent, year) => {
     if (data){
      if (continent != null && continent != "all") {
      filteredCountries = data[year]['countries'].filter(country => country.continent == continent);
     } else{
      filteredCountries = data[year]['countries'];
     }
     }    
     
  }
  $: filterByContinentAndYear(selectedContinent, selectedYear)

</script>

{#if !data}
  <p>Loading the data, please wait...</p>
{:else}
  <div>
    <p>{selectedContinent}</p>
    <Scatterplot data={filteredCountries}/>
    <Controls bind:selectedContinent bind:selectedYear />
  </div>
{/if}
