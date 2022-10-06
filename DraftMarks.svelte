<script>

  export let subjectKey
  export let studentKey

  import {token, draftMarks, showAddDraftMark, showModifyDraftMark, selectedDraftMark} from '../stores'
  import {link, location, push} from 'svelte-spa-router'
  import {fetchDraftMarks} from '../fetch/fetch'
  import {months} from '../utils/utils'

</script>

{#await fetchDraftMarks($token, subjectKey, studentKey) then data}
  <div id="container">
    <div id="title">
        <span>Note ciornă</span>
        <div id="add-button" on:click={() => {$showAddDraftMark = true}}>
          <img src="/img/plus.png" alt="">
        </div>
    </div>

    <div id="content">
      <l>
        {#each $draftMarks as draftMark}
          <li id="element">
            {draftMark.value} - {draftMark.dateDay} {months[draftMark.dateMonth]}
            <span id="edit" on:click={() => {
              $showModifyDraftMark = true
              $selectedDraftMark = draftMark
              console.log($selectedDraftMark)
            }}>
              edit
            </span>
          </li>
        {/each}
      </l>
    </div>
  </div>
{/await}

<style scoped>
  #container {
    width: var(--width);
 
    margin: auto;
    margin-top: 15px;
    
    color: var(--darkgreen);
    background: var(--lightgreen);
    
    border-radius: var(--border-radius);
    border: var(--border);

    box-sizing: border-box;
    padding: 10px 30px 2.5px 30px;
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

  #edit {
    float: right;
    font-size: 0.9em;
    margin-right: 2px;
    color: var(--darkgreen);
    text-decoration: none;
  }

</style>