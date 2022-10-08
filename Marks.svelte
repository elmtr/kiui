<script>

  export let subjectKey
  export let studentKey

  import {token, marks, showAddMark, average} from '../stores'
  import {fetchMarks} from '../fetch/fetch'
  import {months, calcAverage} from '../utils/utils'
  import { writable } from 'svelte/store'

  console.log(average)

</script>

{#await fetchMarks($token, subjectKey, studentKey) then data}
  <div id="container">
    <div id="title">
        <span>Note</span>
        <div id="add-button" on:click={() => {$showAddMark = true}}>
          <img src="/img/plus.png" alt="">
        </div>
    </div>
    <div id="content">
      <l>
        {calcAverage($marks)}
        {#each $marks as mark}
          <li id="element">
            {mark.value} - {mark.dateDay} {months[mark.dateMonth]}
          </li>
        {/each}
      </l>
    </div>
    {#if $marks.length > 1}
      <div id="average">
        Media: {$average}
      </div>
    {/if}
  </div>
{/await}


<style scoped>
  #container {
    width: var(--width);

    margin: auto;
    margin-top: 15px;
    
    color: var(--darkgreen);
    background: var(--white);
    
    border-radius: var(--border-radius);
    border: var(--border);

    box-sizing: border-box;
    padding: 10px 30px 0 30px;
  }

  #title {
    height: 40px;
    position: relative;
  }

  #title span {
    width: 100%;
    font-family: sans-serif;
    font-size: 1.5em;
    color: var(--darkgreen);
    
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #add-button {
    height: 40px;
    width: 40px;
    background: var(--darkgreen);
    float: right;
    border-radius: 100%;
  }

  #add-button img {
    width: 80%;
    position: relative;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  #content {
    width: 100%;
    
    box-sizing: border-box;
    margin-top: 10px;

    color: var(--darkgreen);
    font-size: 1.3em;
    font-family: var(--sans-serif);
  }

  #element {
    margin-bottom: 15px;
  }

  #average {
    width: 100%;
    font-size: 1.3em;
    font-family: var(--sans-serif);
    color: var(--lightgreen);

    box-sizing: border-box;
    padding-bottom: 15px;
  }

</style>