<script>
  import { pop } from "svelte-spa-router"

  function goBack() {
    pop()
  }

</script>

<div id="header">
  <div id="back-button" on:click={goBack}>
    <img src="/img/left.png" alt="">
  </div>
</div>

<style scoped>
  #header {
    background: var(--white);
    height: 60px;
    width: 100%;
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
</style>