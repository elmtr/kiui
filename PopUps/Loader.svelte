<script>
  import {loading} from '../../stores'
</script>

{#if $loading}
  <div id="shadow">
    <img src="/img/loading.gif" alt="">
  </div>
{/if}

<style scoped>
  #shadow {
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    position: fixed;
    top: 0;
  }

  #shadow img {
    width: 20px;
    height: 20px;

    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>