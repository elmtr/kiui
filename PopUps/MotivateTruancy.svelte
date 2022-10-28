<script>
  import { fetchTruancies } from '../../fetch/fetch'
  import {updateMotivateTruancy} from '../../fetch/update'
  import {showMotivateTruancy, selectedTruancy, token} from '../../stores'
  import {months} from '../../utils/utils'
    import AddButton from '../Inputs/AddButton.svelte'


</script>

{#if $showMotivateTruancy}
  <div id="shadow"></div>
  <div id="window">
     <div id="close" on:click={() => {$showMotivateTruancy = false}}>
      <img src="/img/left-darkgreen.png" alt="">
    </div>
    <div id="title">
      <span>
        Motivează absența de pe data de 
        {$selectedTruancy.dateDay} {months[$selectedTruancy.dateMonth]}
      </span>
    </div>

    <div id="button">
      <AddButton value="Confirmă" onClick={async () => {
        await updateMotivateTruancy($token, $selectedTruancy.key)
        await fetchTruancies($token, $selectedTruancy.subjectKey, $selectedTruancy.studentKey)
        $showMotivateTruancy = false
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
    z-index: 3;
    margin: auto;
  }

  #window {
    width: 90%;
    max-width: 400px;
    height: 95%;
    max-height: 300px;

    background: var(--white);
    border-radius: var(--border-radius);

    position: fixed;

    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 4;
  }

  #close {
    width: 95%;
    height: 40px;
    margin: auto;
    margin-top: 10px;
  }

  #close img {
    height: 95%;

    position: relative;
    top: 50%;
    left: 10px;
    transform: translateY(-50%);
  }

  #title {
    width: 80%;
    height: 40px;
    margin: auto;
  }

  #title span {
    position: relative;
    top: 50%;
    left: 20px;
    right: 20px;
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