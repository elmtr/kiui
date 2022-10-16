<script>
  import {warningMessage} from '../stores'
</script>

{#if $warningMessage !== ""}
  <div id="container">
    <span>⚠ {$warningMessage}</span>
  </div>
{/if}

<style scoped>
  #container {
    width: 90%;
    box-sizing: border-box;
    margin: auto;
    color: var(--yellow);
    font-family: var(--sans-serif);
    font-size: 1em;
    padding: 10px;
  }

</style>