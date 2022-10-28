<script>

  export let subjectKey
  export let studentKey
  export let mod

  import {token, truancies, selectedTruancy, showMotivateTruancy, showAddTruancy} from '../../stores'
  import {fetchTruancies} from '../../fetch/fetch'
  import {months} from '../../utils/utils'
  import { writable } from 'svelte/store'

  let numberTruancies = writable(0)

  function calcNumberTruancies() {
    $numberTruancies = $truancies.length

    return ''
  }

</script>

{#await fetchTruancies($token, subjectKey, studentKey) then data}
  <div id="container">
    <div id="title">
        <div id="title-title">
          <span>{$numberTruancies}</span> 
          {#if $numberTruancies === 1}
            Absență:
          {:else}
            Absențe:
          {/if}
        </div>
        {#if mod}
          <div id="add-button" on:click={() => {$showAddTruancy = true}}>
            <img src="/img/plus.png" alt="">
          </div>
        {/if}
    </div>

    <div id="content">
      {#if $truancies.length > 0}
        <l>
          {calcNumberTruancies()}
          {#each $truancies as truancy}
            <li id="element">
              {truancy.dateDay} {months[truancy.dateMonth]}
              {#if truancy.motivated} 
                <div class="status">
                  motivată
                </div>
              {:else}
                <div class="status">
                  <span
                    on:click={() => {$selectedTruancy = truancy; $showMotivateTruancy = true}}
                    style="color: var(--red); text-decoration: none" 
                  >
                    motivează
                  </span>
                </div>
              {/if}
            </li>
          {/each}
        </l>
      {:else}
        <div id="not-exist">Nu există absențe.</div> 
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
    background: var(--white);
    
    border-radius: var(--border-radius);
    border: var(--border);

    box-sizing: border-box;
    padding: 10px 30px 2.5px 30px;
  }

  #title {
    height: 40px;
    position: relative;
  }

  #title-title {
    width: 100%;
    font-family: sans-serif;
    font-size: 1.5em;
    color: var(--darkgreen);
    
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #title-title span {
    color: var(--lightgreen);
    font-weight: 600;
    margin-right: 10px;

    position: relative;
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

  .status {
    float: right;
    margin-right: 2px;
    color: var(--lightgreen);
  }
</style>