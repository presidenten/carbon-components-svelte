<script>
  import { onMount } from "svelte";

  onMount(() => {
    document.body.classList.add("framed");
    return () => {
      document.body.classList.remove("framed");
    };
  });

  // TODO: [refactor] parse search parameters more reliably
  $: currentTheme = window.location.search.split("?theme=")[1];
  $: document.documentElement.setAttribute("theme", currentTheme);
</script>

<slot />

<style>
  :global(body.framed) {
    min-height: 100vh;
    width: 100%;
    padding: var(--cds-spacing-06) var(--cds-spacing-05);
  }
</style>
