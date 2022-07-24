<script>
	import { MaterialApp, AppBar, Divider, Button, Icon } from "svelte-materialify";

	let theme = "light";

	function toggleTheme() {
	  if (theme === "light") theme = "dark";
	  else theme = "light";
	}
	import { mdiMenu } from "@mdi/js";
</script>

<style>
  main {
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
  }
</style>

<MaterialApp {theme}>
  <AppBar>
    <div slot="icon">
      <Button fab depressed > <!-- on:click={toggleNavigation}> -->
        <Icon  path={mdiMenu}/>
      </Button>
    </div>
    <span slot="title"> Click The Menu </span>
  </AppBar>
	<br />
  <div class="card-background">
      

    <h2 class="mb-4">
      Page 2
    </h2>
    <Divider />
    <br>
    <div class="text-center">
      <a href="/App.svelte">
        <Button class="primary-color">
          Page 1
        </Button>
      </a>
      <Button on:click={toggleTheme}>Toggle Theme</Button>
    </div>
  </div>
</MaterialApp>