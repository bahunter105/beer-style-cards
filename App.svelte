<script>
  import Button from "./Button.svelte";
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
    height: 90vh;
    width: 90vw;
    margin: auto auto auto auto;
  }
</style>

<main>
  <div class="card-background">
    <h1>Hello CodeSandbox</h1>
    <h2>Start editing to see some magic happen!</h2>
    <Button />
    <Card />
  </div>
</main>