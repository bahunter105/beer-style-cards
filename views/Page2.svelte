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
  export let fetchData;
  export let changePage;
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
      Page 2
    </h2>
    <Divider />
    <br>
    <div class="text-center">
        <!-- <Button class="primary-color" on:click = {changePage}>
          Go to Page 2
        </Button> -->
        <Button on:click={toggleTheme}>Toggle Theme</Button>
    </div>
    {#await fetchData() then data}
      {console.log(data)}
      {#each data as item}
        <li>
            <Button on:click = {changePage}>
              {item.subCategory}
            </Button>
          </li>
      {/each}
    {/await}
  </div>