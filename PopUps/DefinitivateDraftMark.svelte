<script>
  import { fetchDraftMarks, fetchMarks } from '../../fetch/fetch'
  import {updateDefinitivateDraftMark} from '../../fetch/update'
  import {showModifyDraftMark, showDefinitivateDraftMark, selectedDraftMark, token} from '../../stores'
  import {calcAverage, months} from '../../utils/utils'
    import AddButton from '../Inputs/AddButton.svelte'

</script>

{#if $showDefinitivateDraftMark}
  <div id="shadow"></div>
  <div id="window">
    <div id="close" on:click={() => {$showDefinitivateDraftMark = false; $showModifyDraftMark = true}}>
      <img src="/img/left.svg" alt="">
    </div>
    <div id="title">
      <span>
        Definitivează nota ciornă
      </span>
    </div>

    <div id="button">
      <AddButton value="Confirmă" onClick={async () => {
        await updateDefinitivateDraftMark($token, $selectedDraftMark.key)
        await fetchDraftMarks($token, $selectedDraftMark.subjectKey, $selectedDraftMark.studentKey)
        let marks = await fetchMarks($token, $selectedDraftMark.subjectKey, $selectedDraftMark.studentKey)
        calcAverage(marks)
        $showDefinitivateDraftMark = false
        $showModifyDraftMark = false
      }} />
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
    max-height: 300px;
    background: var(--white);
    border-radius: var(--border-radius);

    width: 100%;
    height: 100%;
    max-height: none;
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
</style>