<script>
  import { MaterialApp, 
    AppBar, 
    Divider, 
    Button, 
    Icon,
    Card,
    CardTitle,
    CardSubtitle,
    CardActions,
    Row,
    Col } from "svelte-materialify";
  // import Page1 from "./views/Page1.svelte";
  // import Page2 from "./views/Page2.svelte";
  import { mdiMenu, mdiChevronDoubleLeft } from "@mdi/js";
  let theme = "light";
  let mainBeer;
  function toggleTheme() {
    if (theme === "light") theme = "dark";
    else theme = "light";
  }

  async function beerData() {
    const res = await fetch("https://beerstyles-api.herokuapp.com/beerstyles/");
    const data = await res.json();
    if (res.ok) {
      return data;
    } else {
      throw new Error(data);
    }
  }

  function setMainBeer(e) {
    console.log('hi');
    console.log(e)
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

<MaterialApp {theme}>
  <!-- {#if page === 1} -->
    <!-- <AppBar>
      <span slot="title" > Beer Style Cards </span>
    </AppBar> -->
  <!-- {:else} -->
    <!-- <AppBar>
      <div slot="icon">
          <Button fab depressed on:click={toHome}>
            <Icon  path={mdiChevronDoubleLeft}/>
          </Button>
      </div>
      <span slot="title"> {mainBeer} </span>
    </AppBar> -->
  <!-- {/if} -->
	<!-- <br /> -->
  {#await beerData()}
    <p>loading</p>
  {:then beers}
    {#if mainBeer === undefined}
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
        {#each beers as beer}
          <li>
              <Button on:click = {(e) => mainBeer={beer}} >
                {beer.subCategory}
                <!-- {e => console.log("main")} -->
              </Button>
            </li>
        {/each}
      </div>
    {:else}
      <div class="text-center">
        <Button class="primary-color" on:click={toggleTheme}>{mainBeer}</Button>
      </div>
    {/if}

  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</MaterialApp>