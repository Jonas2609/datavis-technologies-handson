<script>
  // Properties

  const continents = ["europe", "asia", "americas", "africa", "all"];
  export let selectedContinent = null;
  export let selectedYear = 0;
  const myArray = Array.from({length: 5}, (_, index) => index);

  const nextYear = () => {
    if (selectedYear == 214) {
        selectedYear = 0;
      } else {
        selectedYear += 1;
      }
  }
  let interval;
  let isPlaying = false;

  const play = () => {
    isPlaying = true;
    interval = setInterval(nextYear, 10);
  };
  const stop = (interval) => {
    clearInterval(interval);
    isPlaying = false;
  };
  const reset = (interval) => {
    stop(interval);
    selectedYear = 0;
  };

</script>

<div class="row">
  <div class="dropdown">
    <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
      Select Continent
    </button>
    <div class="dropdown-menu" aria-labelledby="dropdownMenu2">
      {#each continents as continent}
      <li><button class="dropdown-item" type="button" on:click={() => (selectedContinent = continent)}>{continent.charAt(0).toUpperCase() + continent.slice(1)}</button></li>
      {/each}
    </div>
  </div>
   <div class="btn-group ml-3" role="group" aria-label="Basic example">
    <button type="button" class="btn btn-secondary" on:click={() => (isPlaying ? stop(interval) : play())}>
      {#if isPlaying}
        Stop
      {:else}
        Play
      {/if}
    </button>
    <button type="button" class="btn btn-secondary" on:click={() => reset(interval)}>Reset</button>
    
  </div>
  <div class="progress">
    <div class="progress-bar" role="progressbar" style="width: {selectedYear/214};" aria-valuenow={selectedYear} aria-valuemin="0" aria-valuemax="214">{1800+selectedYear}</div>
  </div>
</div>
