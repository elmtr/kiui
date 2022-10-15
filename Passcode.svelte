<script>
  export let value
</script>

<div id="container">
  <div class="digit-container">
    <div class="digit">
      {#if value[0]}
        <span>*</span>
      {/if}
    </div>
  </div>
  <div class="digit-container">
    <div class="digit">
      {#if value[1]}
        <span>*</span>
      {/if}
    </div>
  </div>
  <div class="digit-container">
    <div class="digit">
      {#if value[2]}
        <span>*</span>
      {/if}
    </div>
  </div>
  <div class="digit-container">
    <div class="digit">
      {#if value[3]}
        <span>*</span>
      {/if}
    </div>
  </div>
</div>

<style scoped>
  #container {
    width: 80%;
    height: 60px;
    display: flex;
    margin: auto;
  }


  .digit-container {
    flex: 25%;
  }

  .digit {
    background: var(--white);
    height: 60px;
    width: 60px;
    border-radius: 30%;
    
    margin: 0;
    position: relative;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  .digit span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);

    color: var(--darkgreen);
    font-family: var(--sans-serif);
    font-size: 2em;
  }
</style>