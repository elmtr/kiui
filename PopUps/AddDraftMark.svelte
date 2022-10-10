<script>
  import { fetchDraftMarks } from '../../fetch/fetch'
  import {postDraftMark} from '../../fetch/set'
  import {showAddDraftMark, d, token} from '../../stores'

  import InputSelect from '../Inputs/InputSelect.svelte'
  import InputSelectMark from '../Inputs/InputSelectMark.svelte'
  import InputSelectMonth from '../Inputs/InputSelectMonth.svelte'
  import SubmitButton from '../Inputs/SubmitButton.svelte'

  let value = 10
  let dateDay = d.getDate()
  let dateMonth = d.getMonth() + 1

  export let params = {}

</script>

{#if $showAddDraftMark}
  <div id="shadow"></div>
  <div id="window">
    <div id="close" on:click={() => {$showAddDraftMark = false}}>
      <img src="/img/close.png" alt="">
    </div>
    <div id="text">Adaugă notă ciornă</div>
    <div id="data">
      <div class="data-row">
        <div class="data-cell">
          <span>Nota: </span>
          <InputSelectMark bind:value={value} list={[...Array(10).keys()]} />
        </div>
      </div>

      <div class="data-row">
        <div class="data-cell">
          <span>Ziua: </span>
          <InputSelect bind:value={dateDay} list={[...Array(31).keys()]} />
        </div>
      </div>

      <div class="data-row">
        <div class="data-cell">
          <span>Luna: </span>
          <InputSelectMonth bind:value={dateMonth} list={[...Array(12).keys()]} />
        </div>
      </div>
    </div>
    <div id="button">
      <SubmitButton value="Adaugă" onClick={async () => {
        await postDraftMark($token, value, dateDay, dateMonth, params.subjectKey, params.studentKey)
        await fetchDraftMarks($token, params.subjectKey, params.studentKey)
        $showAddDraftMark = false
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
  }
  #window {
    width: 90%;
    height: 350px;

    background: var(--white);
    border-radius: var(--border-radius);

    position: fixed;

    margin-left: 5%;
    bottom: 20px;
  }

  #text {
    width: 60%;
    margin: auto;
    margin-top: 20px;
    font-size: 1.3em;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
    text-align: center;
  }

  #close {
    height: 30px;
    width: 30px;
    position: absolute;
    top: 10px;
    right: 10px;
  }

  #close img {
    width: 100%;
    height: 100%;

  }

  #data {
    margin-top: 25px;
    width: 90%;
    margin-left: 5%;
    box-sizing: border-box;
  }

  .data-row {
    width: 100%;
    height: 40px;
    float: left;
    margin-bottom: 10px;
  }

  .data-cell {
    margin-left: 2.5%;
    margin-right: 2.5%;
    float: left;
    color: var(--darkgreen);
    font-size: 1.2em;
    font-family: var(--sans-serif);
  }

  #button {
    width: 90%;

    position: absolute;
    left: 5%;
    bottom: 20px;
  }
</style>