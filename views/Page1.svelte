<script>
 import { MaterialApp, AppBar, Divider, Button, Icon } from "svelte-materialify";
 //  export let theme;
 //  export let page;
 export let title = "Page 1";
 export let toggleTheme;
 export let handleClick;
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
        <Button class="primary-color" on:click = {handleClick}>
          Go to Page 2
        </Button>
        <Button on:click={toggleTheme}>Toggle Theme</Button>
    </div>
  </div>