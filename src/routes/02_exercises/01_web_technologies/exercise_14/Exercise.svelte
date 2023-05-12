<style>
  .selected {
    background-color: yellow;
  }
</style>

<script>
  let current = "";

  function handleClick(button) {
    if (button.classList.contains("selected")) {
      button.classList.remove("selected");
      current = "";
    } else {
      current = button.textContent.toLowerCase();
      resetSelected();
      button.classList.add("selected");
    }
  }

  function resetSelected() {
    const buttons = document.querySelectorAll(".btn");
    buttons.forEach((button) => {
      button.classList.remove("selected");
    });
  }
</script>

<button class="btn btn-secondary" on:click={() => handleClick($event.target)}>
  Messi
</button>

<button class="btn btn-secondary" on:click={() => handleClick($event.target)}>
  Ronaldo
</button>

<button class="btn btn-secondary" on:click={() => handleClick($event.target)}>
  Neymar
</button>
