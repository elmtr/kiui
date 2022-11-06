<script>

  export let subjectKey
  export let studentKey
  export let mod

  import {token} from '../../stores'
  import {writable} from 'svelte/store'
  import {fetchPoints} from '../../fetch/fetch'

  let pointsValue = writable(0);

  async function getPoints() {
    let data = await fetchPoints($token, subjectKey, studentKey)
    pointsValue.set(data.value)

    return data
  }

  async function decreasePoints(key) {
    await updateDecreasePoints($token, key)
    pointsValue.set($pointsValue - 1)
  }

  async function increasePoints(key) {
    await updateIncreasePoints($token, key)    
    pointsValue.set($pointsValue + 1)
  }

  import {
    updateDecreasePoints, 
    updateIncreasePoints
  } from '../../fetch/update'

</script>

{#await getPoints() then points}
  <div id="container">
    <div id="points">
      Puncte: <span>{$pointsValue}</span>
    </div>

    {#if mod}
      <div id="buttons">
        <div class="button" on:click={() => {decreasePoints(points.key)}}>
          <img src="/img/minus.svg" alt="">
        </div>

        <div class="button" on:click={() => {increasePoints(points.key)}} style="left: 57px;">
          <img src="/img/plus.svg" alt="">
        </div>
      </div>
    {/if}
  </div>
{/await}

<style scoped>
  #container {
    width: var(--width);
    height: 65px;
    margin: auto;
    background: var(--darkgreen);
    border-radius: var(--border-radius);
    border: var(--border);
    margin-top: 10px;
    position: relative;
  }  

  #points {   
    font-family: var(--sans-serif);
    font-size: 1.5em;
    color: var(--lightgreen); 
    margin: 0;
    position: absolute;
    top: 50%;
    left: 15px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #points span {
    font-weight: 600;
  }

  #buttons {
    width: 120px;
    height: 100%;
    position: relative;
    float: right;
    margin-right: 10px;
  }

  .button {
    width: 40px;
    height: 40px;
    background: var(--lightgreen);
    color: var(--white);
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
    border-radius: 100%;
    border: var(--border);
  }

  .button img {
    width: 55%;
    position: relative;
    filter: var(--white-filter);
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
</style>