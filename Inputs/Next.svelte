<script>
  export let onClick
</script>

<div id="container" on:click={onClick}>
  <span>Continuă</span>
</div>

<style scoped>
  #container {
    width: 120px;
    height: 60px;
    border-radius: var(--border-radius);
    background: var(--darkgreen);

    position: fixed;
    right: 20px;
    bottom: 20px;

    color: var(--lightgreen);
  }

  #container span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);

    font-family: var(--sans-serif);
    font-size: 15px;
  }

</style>