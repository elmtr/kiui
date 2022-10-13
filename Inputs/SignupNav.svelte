<script>
  import { push } from "svelte-spa-router"

  export let previous
  export let next
</script>

{#if previous !== ""}
  <div on:click={() => {push(previous)}}>prev</div>
{/if}

<div on:click={() => {push(next)}}>next</div>


