<script>
  export let onClick
  export let active

  import {loading} from '../../stores'
  
</script>

{#if active && !$loading} 
  <div class="container" on:click={onClick}>
    <span>Continuă</span>
  </div>
{:else if $loading}
  <div class="container active-false">
    <img src="/img/loading.gif" alt="">
    <span style="left: 60%">Continuă</span>
  </div>
{:else}
  <div class="container active-false">
    <span>Continuă</span>
  </div>
{/if}

<style scoped>
  .container {
    width: 120px;
    height: 60px;
    border-radius: 300px;
    background: var(--lightgreen);

    position: fixed;
    right: 20px;
    bottom: 20px;

    color: var(--darkgreen);
  }

  .active-false {
    color: var(--darkgreen-transparent);
    background: var(--lightgreen-transparent);
  }

  .container span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);

    font-family: var(--sans-serif);
    font-size: 15px;
  }

  .container img {
    width: 20px;
    
    position: absolute;
    top: 50%;
    left: 20%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
</style>