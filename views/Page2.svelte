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
  import { mdiMenu, mdiChevronDoubleLeft } from "@mdi/js";
  export let fetchData;
  export let toggleTheme;
  export let changePage;
  export let beer_data;
  export let mainBeer;

  function toHome() {
    changePage(1);
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

  <AppBar>
    <div slot="icon">
        <Button fab depressed on:click={toHome}>
          <Icon  path={mdiChevronDoubleLeft}/>
        </Button>
    </div>
    <span slot="title"> {mainBeer.subCategory} </span>
  </AppBar>
	<br />
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