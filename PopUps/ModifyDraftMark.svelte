<script>
  import { fetchDraftMarks } from '../../fetch/fetch'
  import { updateModifyDraftMark } from '../../fetch/update'
  import {showModifyDraftMark, showDefinitivateDraftMark, selectedDraftMark, d, token} from '../../stores'
  
  import AddButton from '../Inputs/AddButton.svelte'
  import InputSelectDate from '../Inputs/InputSelectDate.svelte'
  import InputSelectMark from '../Inputs/InputSelectMark.svelte'

  import {writable} from 'svelte/store'
    

  let value = writable(10)
  let dateDay = writable(1)
  let dateMonth = writable(1)
  $: {
    $value = $selectedDraftMark.value
    $dateDay = $selectedDraftMark.dateDay
    $dateMonth = $selectedDraftMark.dateMonth
  }

  export let params = {}
</script>

{#if $showModifyDraftMark}
  <div id="shadow"></div>
  <div id="window">
    <div id="close" on:click={() => {$showModifyDraftMark = false}}>
      <img src="/img/left.svg" alt="">
    </div>
    <div id="title">
      <span>
        Modifică nota ciornă
      </span>
    </div>

    <InputSelectMark bind:value={value} />
    <InputSelectDate bind:month={$dateMonth} bind:day={$dateDay} />
   
    <div id="button">
      <div id="definitivate" on:click={() => {
        $showDefinitivateDraftMark = true; 
        $showModifyDraftMark = false
      }}>
        Definitiveaza nota
      </div>
      <AddButton value="Modifică" onClick={async () => {
        await updateModifyDraftMark($token, 
          $selectedDraftMark.key, 
          $value, 
          $dateDay, 
          $dateMonth, 
          params.subjectKey, 
          params.studentKey
        )
        await fetchDraftMarks($token, params.subjectKey, params.studentKey)
        $showModifyDraftMark = false
      }}/>
    </div>
  </div>
{/if}

<style scoped>
  #shadow {
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    top: 0;
    left: 0;
    z-index: 7;
    margin: auto;
  }

  #window {
    width: 90%;
    max-width: 400px;
    height: 95%;
    background: var(--white);
    border-radius: var(--border-radius);

    width: 100%;
    height: 100%;
    border-radius: 0;
    background: var(--offwhite);

    position: fixed;

    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 8;
  }

  #close {
    width: 95%;
    height: 40px;
    margin: auto;
    margin-top: 10px;
  }

  #close img {
    height: 95%;
    filter: var(--darkgreen-filter);

    position: relative;
    top: 50%;
    left: 10px;
    transform: translateY(-50%);
  }

  #title {
    width: 95%;
    height: 40px;
    margin: auto;
  }

  #title span {
    position: relative;
    top: 50%;
    left: 20px;
    transform: translateY(-50%);
    font-size: 1.5em;
    font-weight: 600;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
  }

  #button {
    position: absolute;
    bottom: 10px;
    width: 90%;
    left: 5%;
  }

  #definitivate {
    color: var(--lightgreen);
    margin: 20px;
    font-size: 1.2em;
    font-family: var(--sans-serif);
    /* text-decoration: underline; */
  }
</style>