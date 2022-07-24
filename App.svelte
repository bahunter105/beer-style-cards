<script>
						import { MaterialApp, AppBar, Divider, Button, Icon } from "svelte-materialify";
						import Page1 from "./views/Page1.svelte";
						import Page2 from "./views/Page2.svelte";
						import { mdiMenu } from "@mdi/js";
            let theme = "light"
            let page = Page1
            
						function toggleTheme() {
						  if (theme === "light") theme = "dark";
						  else theme = "light";
						  // console.log("Hi");
						  // theme = "dark";
						}

						function handleClick() {
						  if (page === Page1) page = Page2;
						  else page = Page1;
						  // console.log("What?");
						  // page = Page1;
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
  <svelte:component this={page}
    {toggleTheme}
    {handleClick}
  />
</MaterialApp>