<script>
  import {loading} from '../stores'
</script>

{#if $loading}
  <div id="loading">
    <img src="/img/loading.gif" alt="">
  </div>
{/if}

<style scoped>
  #loading {
    width: 100%;
    height: 60px;
    position: relative;
  }

  #loading img {
    width: 20px;
    height: 20px;
    position: absolute;

    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
</style>