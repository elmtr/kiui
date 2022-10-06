<script>
  import { fetchDraftMarks, fetchMarks } from '../fetch/fetch'
  import {updateDefinitivateDraftMark} from '../fetch/update'
  import {showModifyDraftMark, showDefinitivateDraftMark, selectedDraftMark, token} from '../stores'
  import {calcAverage, months} from '../utils/utils'

</script>

{#if $showDefinitivateDraftMark}
  <div id="shadow"></div>
  <div id="window">
    <div id="text">Definitivează nota ciornă {$selectedDraftMark.value} de pe 
      {$selectedDraftMark.dateDay} {months[$selectedDraftMark.dateMonth]}?
    </div>

    <div id="buttons">
      <div class="button" style="background: var(--gray);" on:click={() => {
        $showDefinitivateDraftMark = false
        $showModifyDraftMark = true
      }}>
        <span>Nu</span>
      </div>
      <div class="button" style="border: var(--border);" 
        on:click={async () => {
          await updateDefinitivateDraftMark($token, $selectedDraftMark.key)
          await fetchDraftMarks($token, $selectedDraftMark.subjectKey, $selectedDraftMark.studentKey)
          let marks = await fetchMarks($token, $selectedDraftMark.subjectKey, $selectedDraftMark.studentKey)
          calcAverage(marks)
          $showDefinitivateDraftMark = false
          $showModifyDraftMark = false
        }}
      >
        <span>Da</span>
      </div>
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
  }
  #window {
    width: 90%;
    height: 200px;

    background: var(--white);
    border-radius: var(--border-radius);

    position: fixed;

    margin-left: 5%;
    bottom: 20px;
  }

  #text {
    width: 70%;
    margin: auto;
    margin-top: 20px;
    font-size: 1.3em;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
    text-align: center;
  }

  #buttons {
    width: 100%;
    height: 40px;

    position: absolute;
    bottom: 20px;
  }

  .button {
    width: 45%;
    height: 100%;
    margin-left: 2.5%;
    background: var(--lightgreen);
    float: left;
    position: relative;

    border-radius: var(--border-radius);
  }

  .button span {
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);

    width: 100%;
    text-align: center;
    font-size: 1.3em;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
  }
</style>