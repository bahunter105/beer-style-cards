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
  //  export let theme;
  export let fetchData;
  export let toggleTheme;
  export let beer_data;
  export let changePage;
  export let mainBeer;
  function setMainBeer(event) {
    mainBeer = event.item;
    changePage(2);
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
    <span slot="title"> Beer Style Cards </span>
  </AppBar>
	<br />
  <div class="card-background">
    <h2 class="mb-4">
      Page 1
    </h2>
    <Divider />
    <br>
    <div class="text-center">
        <Button class="primary-color" on:click={toggleTheme}>Toggle Theme</Button>
    </div>
      {#each beer_data as item}
        <li>
            <Button on:click = {setMainBeer}>
              {item.subCategory}
            </Button>
          </li>
      {/each}
  </div>