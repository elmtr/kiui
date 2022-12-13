<script>

  export let subjectKey
  export let studentKey
  export let mod

  import {token, draftMarks, showAddDraftMark, showModifyDraftMark, selectedDraftMark} from '../../stores'
  import {fetchDraftMarks} from '../../fetch/fetch'
  import {months} from '../../utils/utils'

</script>

{#await fetchDraftMarks($token, subjectKey, studentKey) then data}
  <div id="container">
    <div id="title">
        <span>Note ciornă</span>
        {#if mod}
          <div id="add-button" on:click={() => {$showAddDraftMark = true}}>
            <img src="/img/plus.svg" alt="">
          </div>
        {/if}
    </div>

    <div id="content">
      {#if $draftMarks.length > 0}
        <l>
          {#each $draftMarks as draftMark}
            <li id="element">
              nota {draftMark.value} pe {draftMark.dateDay} {months[draftMark.dateMonth]}
              {#if mod}
                <span id="edit" on:click={() => {
                  $showModifyDraftMark = true
                  $selectedDraftMark = draftMark
                }}>
                  edit
                </span>
              {/if}
            </li>
          {/each}
        </l>
      {:else}
        <div id="not-exist">Nu există note ciornă</div>
      {/if}
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
    width: 55%;
    filter: var(--white-filter);
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

  #edit {
    float: right;
    font-size: 0.9em;
    margin-right: 2px;
    color: var(--darkgreen);
    text-decoration: none;
  }
</style>