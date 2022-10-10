<script>

  export let subjectKey
  export let studentKey
  export let mod

  import {token, marks, showAddMark, average} from '../../stores'
  import {fetchMarks} from '../../fetch/fetch'
  import {months, calcAverage} from '../../utils/utils'

  console.log(average)

</script>

{#await fetchMarks($token, subjectKey, studentKey) then data}
  <div id="container">
    <div id="title">
        <span>Note</span>
        {#if mod}
          <div id="add-button" on:click={() => {$showAddMark = true}}>
            <img src="/img/plus.png" alt="">
          </div>
        {/if}
    </div>
    <div id="content">
      {#if $marks.length > 0}
        <l>
          {calcAverage($marks)}
          {#each $marks as mark}
            <li id="element">
              {mark.value} pe {mark.dateDay} {months[mark.dateMonth]}
            </li>
          {/each}
        </l>
      {:else}
        <div id="not-exist">Nu există note.</div> 
      {/if}
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

  #not-exist {
    text-align: center;
    width: 100%;
    margin: auto;
    color: var(--darkgreen);
    font-weight: 600;
    font-size: 0.9em;
    margin-top: 10px;
    margin-bottom: 10px;
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