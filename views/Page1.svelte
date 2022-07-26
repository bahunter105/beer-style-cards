<script>
  import {
    MaterialApp,
    AppBar,
    Divider,
    Button,
    Icon,
    Card,
    CardTitle,
    CardSubtitle,
    CardActions,
    Row,
    Col
  } from "svelte-materialify";
  //  export let theme;
  export let toggleTheme;
  export let beer_data;
  export let changePage;
  export let mainBeer;
  function setMainBeer(item) {
    mainBeer = item;
    changePage;
  }
</script>

<style>
  .card-background {
    background-color: greenyellow;
    border-radius: 5%;
    height: 80vh;
    width: 90vw;
    margin: auto auto auto auto;
  }
</style>

  <div class="card-background">
    <h2 class="mb-4">
      Page 1
    </h2>
    <Divider />
    <br>
    <div class="text-center">
        <Button class="primary-color" on:click = {changePage}>
          Go to Page 2
        </Button>
        <Button on:click={toggleTheme}>Toggle Theme</Button>
    </div>
      {console.log(mainBeer)}
      {#each beer_data as item}
        <li>
            <Button on:click = {setMainBeer(item)}>
              {item.subCategory}
            </Button>
          </li>
      {/each}
  </div>