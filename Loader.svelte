<script>
  import {loading} from '../stores'
</script>

{#if $loading}
  <div id="loader">
    <img src="/img/loading.gif" alt="">
  </div>
{/if}

<style>
  #loader {
    background: var(--offwhite);
    position: absolute;
    z-index: 5;
    width: 100%;
    height: 80%;
    margin-top: -5px;
  }

  #loader img {
    width: 25px;
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>