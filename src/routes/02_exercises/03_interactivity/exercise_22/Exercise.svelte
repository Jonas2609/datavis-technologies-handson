<script>
    let count = 0;
</script>
  <div>
    <button type="button" class="btn btn-outline-primary" on:click={() => (count += 1)}> {count}</button>
    <p>Pressme</p>
  </div>
  
  <div>
    <button type="button" class="btn btn-outline-primary" on:click={() => (count = 0)}>Reset</button>
    
  </div>


