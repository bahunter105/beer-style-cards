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
  export let toggleTheme;
  export let changePage;
  export let beer_data;
  export let mainBeer;
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
      {mainBeer.subCategory}
    </h2>
    <Divider />
    <br>
    <div class="text-center">
        <Button on:click={toggleTheme}>Toggle Theme</Button>
    </div>
  </div>