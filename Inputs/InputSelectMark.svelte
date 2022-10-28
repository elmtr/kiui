<script>
  import { writable } from "svelte/store"

  export let value = writable(0);

  function changeValue(n) {
    $value = n
  }

</script>

<div id="container">
  <div id="title">Nota:</div>
  <div class="row">
    <div class="element">
      <div class="mark selected-{$value === 1}" on:click={() => changeValue(1)}>
        <span>1</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 2}" on:click={() => changeValue(2)}>
        <span>2</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 3}" on:click={() => changeValue(3)}>
        <span>3</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 4}" on:click={() => changeValue(4)}>
        <span>4</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 5}" on:click={() => changeValue(5)}>
        <span>5</span>
      </div>
    </div>
  </div>
  <div class="row">
    <div class="element">
      <div class="mark selected-{$value === 6}" on:click={() => changeValue(6)}>
        <span>6</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 7}" on:click={() => changeValue(7)}>
        <span>7</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 8}" on:click={() => changeValue(8)}>
        <span>8</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 9}" on:click={() => changeValue(9)}>
        <span>9</span>
      </div>
    </div>
    <div class="element">
      <div class="mark selected-{$value === 10}" on:click={() => changeValue(10)}>
        <span>10</span>
      </div>
    </div>
  </div>
</div>

<style scoped>
  #container {
    width: 95%;
    /* height: 100px; */
    margin: auto;
    margin-top: 10px;
    box-sizing: border-box;
    padding: 10px 0;
  }

  #title {
    width: 100%;
    height: 20px;
    font-family: var(--sans-serif);
    font-size: 1.2em;
    box-sizing: border-box;
    padding: 0 0 0 15px;
    margin-bottom: 10px;
  }

  .row {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 10px;
  }

  .element {
    flex: 20%;
    height: 55px;
    position: aboslute;
  }

  .mark {
    width: 55px;
    height: 55px;
    border-radius: 13px;

    position: relative;
    left: 50%;
    transform: translateX(-50%);
  }

  .mark span {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    color: var(--lightgreen);
    font-family: var(--sans-serif);
    font-size: 1.4em;
  }

  .selected-true {
    background: var(--darkgreen);
  }
</style>