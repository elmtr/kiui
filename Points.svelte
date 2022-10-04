<script>

  export let subjectKey
  export let studentKey

  import {token} from '../stores'
  import {writable} from 'svelte/store'
  import {fetchPoints} from '../fetch/fetch'

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
  } from '../fetch/update'

</script>

<h1>points</h1>
{#await getPoints() then points}
  <button on:click={() => {decreasePoints(points.key)}}>
    -
  </button>
  {$pointsValue}
  <button on:click={() => {increasePoints(points.key)}}>
    +
  </button>
{/await}
