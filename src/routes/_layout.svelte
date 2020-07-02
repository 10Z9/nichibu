<script>
  import Nav from "../components/Nav/Nav.svelte";

  export let segment;
</script>

<style>
  header {
    top: 0;
    height: 0;
    position: relative;
    z-index: 1000;
  }

  main {
    position: relative;
  }
</style>

<header>
  <Nav {segment} />
</header>

<main>
  <slot />
</main>
