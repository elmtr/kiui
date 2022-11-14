<script>
  export let value
  export let length
  export let okButton = true
  export let onClick
  
  function addDigit(n) {
    if (value.length < length) {
      value += n
    }
  }

  function removeDigit() {
    value = value.substr(0, value.length - 1)
  }

</script>

<div class="row">
  <div class="cell">
    <button class="key" on:click={() => {addDigit(1)}}>
      <div>1</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(2)}}>
      <div>2</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(3)}}>
      <div>3</div>
    </button>
  </div>
</div> 
<div class="row">
  <div class="cell">
    <button class="key" on:click={() => {addDigit(4)}}>
      <div>4</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(5)}}>
      <div>5</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(6)}}>
      <div>6</div>
    </button>
  </div>
</div> 
<div class="row">
  <div class="cell">
    <button class="key" on:click={() => {addDigit(7)}}>
      <div>7</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(8)}}>
      <div>8</div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(9)}}>
      <div>9</div>
    </button>
  </div>
</div> 
<div class="row">
  <div class="cell">
    <button class="key" style="color: var(--lightgreen);" on:click={() => {removeDigit()}}>
      <div>
        <img src="/img/backspace.svg" alt="" style="width: var(" >
      </div>
    </button>
  </div>
  <div class="cell">
    <button class="key" on:click={() => {addDigit(0)}}>
      <div>0</div>
    </button>
  </div>
  <div class="cell">
    {#if okButton}
      <button class="key" style="color: var(--lightgreen);" on:click={onClick}>
        <div style="color: var(--darkgreen);">ok</div>
      </button>
    {/if}
  </div>
</div> 

<style scoped>
  .row {
    box-sizing: border-box;
    height: 60px;
    width: 80%;
    margin: auto;
    margin-bottom: 20px;
    display: flex;
    flex-wrap: wrap;
  }

  .cell {
    flex: 33%;
    /* background: blue; */
  }

  .key {
    margin: auto;
    width: 60px;
    height: 60px;

    position: relative;
    left: 50%;
    transform: translateX(-50%);

    border-radius: 300px;

    outline: none;
    border: none;
    background: var(--offwhite);
  }

  .key div {
    width: 100%;
    text-align: center;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
    font-size: 1.3em;

    margin: 0;
    position: absolute;
    top: 50%;
    left: 0;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  .key div img {
    width: 30px;
    filter: var(--darkgreen-filter);
  }
</style>