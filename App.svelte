<script>
  import { MaterialApp, AppBar, Divider, Button, Icon } from "svelte-materialify";
  import Page1 from "./views/Page1.svelte";
  import Page2 from "./views/Page2.svelte";
  import { mdiMenu, mdiChevronDoubleLeft } from "@mdi/js";
  let theme = "light";
  const pages = [Page1, Page2];
  let page = 1;
  let beer_data;
  let mainBeer;
  function toggleTheme() {
    if (theme === "light") theme = "dark";
    else theme = "light";
    console.log("hi");
  }

  function changePage(number) {
    // if (!page === number) page = 2;
    // else page = 1;
    page = number;
    console.log(number);
  }

  async function fetchData() {
    const res = await fetch("https://beerstyles-api.herokuapp.com/beerstyles/");
    const data = await res.json();
    if (res.ok) {
      beer_data = data;
      mainBeer = beer_data[0];
      return data;
    } else {
      throw new Error(data);
    }
  }
</script>

<style>
</style>

<MaterialApp {theme}>
  {#if page === 1}
    <AppBar>
      <span slot="title" > Beer Style Cards </span>
    </AppBar>
  {:else}
    <AppBar>
      <div slot="icon">
          <Button fab depressed on:click={changePage(1)}>
            <!-- <Icon  path={mdiMenu}/> -->
            <Icon  path={mdiChevronDoubleLeft}/>
          </Button>
      </div>
      <span slot="title"> {mainBeer} </span>
    </AppBar>
  {/if}
	<br />
  {#await fetchData()}
    <p>loading</p>
  {:then item}
    <svelte:component this={pages[page-1]}
      {toggleTheme}
      {changePage}
      {fetchData}
      {beer_data}
      {mainBeer}
    />
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</MaterialApp>