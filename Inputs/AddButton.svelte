<script>

  export let value
  export let onClick

  import {loading} from '../../stores'

</script>


{#if $loading}
  <div id="submit">
    <img src="img/loading.gif" alt="">
  </div>
{:else}
  <div id="submit" on:click={onClick}>
    <span>{value}</span>
  </div>
{/if}

<style scoped>
  #submit {
    width: 100%;
    height: 45px;
    background: var(--darkgreen);
    border: none;
    border: var(--border);
    border-radius: var(--border-radius);
    position: relative;
  }

  #submit:focus-visible {
    border: var(--border);
  }

  #submit span {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: var(--lightgreen);
    font-size: 1em;
    font-family: var(--sans-serif);
  }

  #submit img {
    width: 20px;
    filter: var(--lightgreen-filter);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>