<script>
  import {months} from '../../utils/utils'

  let daysInt = [...Array(31).keys()]
  let monthsInt = [...Array(12).keys()]

  export let month
  export let day

</script>

<div id="container">
  <div id="title">Ziua și luna:</div>
  <select class="select" bind:value={day}>
    {#each daysInt as item} 
      <option class="option"  value={item + 1}>
        {item + 1}
      </option>
    {/each}
  </select>

  <select class="select" bind:value={month} style="width: 50%; max-width: 100px; margin-left: 10px;">
    {#each monthsInt as item} 
      <option class="option"  value={item + 1}>
        {months[item + 1]}
      </option>
    {/each}
  </select>
</div>

<style scoped>
  #container {
    width: 95%;
    margin: auto;
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

  .select {
    background: var(--white);
    color: var(--darkgreen);
    width: 30%;
    max-width: 80px;
    height: 40px;
    border-radius: var(--border-radius);
    border: var(--border);
    font-family: var(--sans-serif);

    margin-left: 10px;

    float: left;

    box-sizing: border-box;
    padding-left: 10px;
  }

  .select:focus-visible {
    outline: none;
  }

  .option {
    background: var(--white);
    border-radius: bar(--border-radius); 
    height: 30px;
  }
</style>