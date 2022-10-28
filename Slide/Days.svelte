<script>
  import { onMount } from 'svelte'  
  import {today} from '../../stores'

  export let day

  let daysString = ['', 'Luni', 'Marți', 'Miercuri', 'Joi', 'Vineri']

  onMount(() => {
    if ($today > 5) {
      day.set(1)
    } else day.set($today)
  })

</script>

<div id="container">
  <div id="left" on:click={() => {
    if ($day === 1) {
      day.set(5)
    } else {
      day.update(value => value - 1)
    }
  }}>
    <img src="/img/left-lightgreen.png" alt="">
  </div>

  <span id="name">
    {daysString[$day]}
  </span>

  <div id="right" on:click={() => {
    if ($day === 5) {
      day.set(1)
    } else {
      day.update(value => value + 1)
    }
  }}>
    <img src="/img/right-lightgreen.png" alt="">
  </div>
</div>

<style scoped>
  #container {
    width: var(--width);
    height: 60px;
    background: var(--darkgreen);
    border-radius: var(--border-radius);
    border: var(--border);
    margin: auto;
    margin-top: 20px;
    box-shadow: 0 1px 5px var(--gray);


    position: relative;
  }

  #left {
    float: left;
    height: 100%;
    width: 60px;
    position: relative;
  }

  #left img {
    width: 70%;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 5px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #right {
    float: right;
    height: 100%;
    width: 60px;
    position: relative;
  }

  #right img {
    width: 70%;
    margin: 0;
    position: absolute;
    top: 50%;
    right: 5px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #name {
    box-sizing: border-box;
    color: var(--lightgreen);
    font-size: 1.6em;
    font-family: var(--sans-serif);
    font-weight: 600;

    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
</style>