<script>
  export let onClick
</script>

<div id="container" on:click={onClick}>
  <img src="/img/back.svg" alt="">
  <span>Inapoi</span>
</div>

<style scoped>
  #container {
    width: 120px;
    height: 60px;
    border-radius: var(--border-radius);

    position: fixed;
    left: 20px;
    bottom: 20px;

  }

  #container img {
    width: 25px;
    filter: var(--darkgreen-filter);

    position: absolute;
    top: 50%;
    left: 15px;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
  
  #container span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
    
    color: var(--darkgreen);
    font-family: var(--sans-serif);
    font-size: 15px;
  }

</style>