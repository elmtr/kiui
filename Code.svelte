<script>
  export let value
</script>

<div id="container">
  <div class="flank" style="margin-left: 5%;">
    <div class="digit-container">
      <div class="digit">
        {#if value[0]}
          <span>{value[0]}</span>
        {:else}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
    <div class="digit-container">
      <div class="digit">
        {#if value[1]}
          <span>{value[1]}</span>
        {:else if value[0]}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
    <div class="digit-container">
      <div class="digit">
        {#if value[2]}
          <span>{value[2]}</span>
        {:else if value[1]}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
  </div>

  <div id="divider-container">
    <div id="divider"></div>
  </div>

  <div class="flank" style="margin-right: 5%;">
    <div class="digit-container">
      <div class="digit">
        {#if value[3]}
          <span>{value[3]}</span>
        {:else if value[2]}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
    <div class="digit-container">
      <div class="digit">
        {#if value[4]}
          <span>{value[4]}</span>
        {:else if value[3]}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
    <div class="digit-container">
      <div class="digit">
        {#if value[5]}
          <span>{value[5]}</span>
        {:else if value[4]}
          <span id="blink">|</span>
        {/if}
      </div>
    </div>
  </div>
</div>

<style scoped>
  #container {
    width: 100%;
    height: 50px;
  }
  .flank {
    width: 40%;
    float: left;

    display: flex;
    flex-wrap: wrap;
  }

  .digit-container {
    flex: 33%;
  }

  .digit {
    background: var(--white);
    height: 45px;
    width: 45px;
    border-radius: 30%;

    position: relative;
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

  #divider-container {
    width: 10%;
    height: 50px;
    float: left;
    position: relative;
  }

  #divider {
    height: 5px;
    width: 20px;
    float: left;
    background: var(--darkgreen);
    border-radius: var(--border-radius);

    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  #blink {
    animation: blinker 1s linear infinite;
  }

  @keyframes blinker {
    50% {
      opacity: 0;
    }
  }
</style>