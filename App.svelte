<script>
  import { MaterialApp, AppBar, Divider, Button, Icon } from "svelte-materialify";
  import Page1 from "./views/Page1.svelte";
  import Page2 from "./views/Page2.svelte";
  import { mdiMenu } from "@mdi/js";
  let theme = "light";
  const pages = [Page1, Page2];
  let page = 1;

  function toggleTheme() {
    if (theme === "light") theme = "dark";
    else theme = "light";
    // console.log("Hi");
    // theme = "dark";
  }

  function handleClick() {
    if (page === 1) page = 2;
    else page = 1;
    // console.log("What?");
    // page = Page1;
  }

  function changePage() {
    page = 2;
  }

  async function fetchData() {
    const res = await fetch("https://beerstyles-api.herokuapp.com/beerstyles/");
    const data = await res.json();

    if (res.ok) {
      return data;
    } else {
      throw new Error(data);
    }
  }
</script>

<style>
  /* main {
                          font-family: sans-serif;
                          text-align: center;
                          display: flex;
                          height: 100vh;
                          width: 100vw;
                        }

                        .card-background {
                          background-color: greenyellow;
                          border-radius: 5%;
                          height: 80vh;
                          width: 90vw;
                          margin: auto auto auto auto;
                        } */
</style>

<MaterialApp {theme}>
  <AppBar>
    <div slot="icon">
      <Button fab depressed > <!-- on:click={toggleNavigation}> -->
        <Icon  path={mdiMenu}/>
      </Button>
    </div>
    <span slot="title"> {page} </span>
  </AppBar>
	<br />
  {#await fetchData()}
  <p>loading</p>
  {:then items}
    <svelte:component this={pages[page-1]}
      {toggleTheme}
      {handleClick}
      {fetchData}
      {changePage}
    />
    <!-- {#each items as item}
      <li>{item.subCategory}</li>
    {/each} -->
  {:catch error}
    <p style="color: red">{error.message}</p>
  {/await}
</MaterialApp>