<script>
  import {errorMessage} from '../stores'
</script>

{#if $errorMessage !== ""}
  <div id="container">
    <span>❗ {$errorMessage}</span>
  </div>
{/if}

<style scoped>
  #container {
    width: 90%;
    box-sizing: border-box;
    margin: auto;
    color: var(--red);
    font-family: var(--sans-serif);
    font-size: 1em;
    padding: 10px;
  }

</style>