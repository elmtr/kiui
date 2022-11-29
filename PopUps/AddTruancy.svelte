<script>
  import { fetchTruancies } from '../../fetch/fetch'
  import {postTruancy} from '../../fetch/set'
  import {showAddTruancy, d, token} from '../../stores'
  import AddButton from '../Inputs/AddButton.svelte'
  import InputSelectDate from '../Inputs/InputSelectDate.svelte'

  let dateDay = d.getDate()
  let dateMonth = d.getMonth() + 1

  export let params = {}

</script>

{#if $showAddTruancy}
  <div id="shadow"></div>
  <div id="window">
    <div id="close" on:click={() => {$showAddTruancy = false}}>
      <img src="/img/left.svg" alt="">
    </div>
    <div id="title">
      <span>
        Adaugă o absență
      </span>
    </div>

    <br><br>
    <InputSelectDate bind:month={dateMonth} bind:day={dateDay} />

    <div id="button">
      <AddButton value="Confirmă" onClick={async () => {
        await postTruancy($token, dateDay, dateMonth, params.subjectKey, params.studentKey)
        await fetchTruancies($token, params.subjectKey, params.studentKey)
        $showAddTruancy = false
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
    border-radius: var(--border-radius);
    background: var(--white);

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
</style>