<script>
  import { pop } from "svelte-spa-router"
</script>

<div id="header">
  <div id="back-button" on:click={() => {pop()}}>
    <img src="/img/left.svg" alt="">
  </div>
</div>

<div id="spacing"></div>

<style scoped>
  #header {
    background: var(--offwhite);
    height: 60px;
    width: 100%;
    position: fixed;
    top: 0;
  }

  #back-button {
    height: 100%;
    width: 50px;
    /* background: red; */
    position: relative;
  }

  #back-button img {
    width: 90%;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 10px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #spacing {
    height: 60px;
  }
</style>