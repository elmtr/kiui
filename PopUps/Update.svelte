<script>

  import {onMount} from 'svelte'
  import {loginUpdate} from '../../fetch/login'
  import {info, loading, errorMessage, showUpdate} from '../../stores'
    
  // kiui
  import KeyPad from '../../kiui/Inputs/KeyPad.svelte'
  import KeyPadOS from '../../kiui/Inputs/KeyPadOS.svelte'
  import Heading from '../../kiui/Heading.svelte'
  import ErrorMessage from '../../kiui/ErrorMessage.svelte'
  import Loading from '../../kiui/Loading.svelte'

  let passcode = ""

  onMount(() => {
    $loading = false
    $errorMessage = ""
  })

</script>

{#if $showUpdate}
  <div id="page">
    <Heading title="Bună, {$info.firstName} 👋" />
    <div id="container">
      <div id="passcode">
        <div class="digit-container">
          {#if passcode.length > 0}
            <div class="digit digit-on"></div>
          {:else}
            <div class="digit"></div>
          {/if}
        </div>

        <div class="digit-container">
          {#if passcode.length > 1}
            <div class="digit digit-on"></div>
          {:else}
            <div class="digit"></div>
          {/if}
        </div>

        <div class="digit-container">
          {#if passcode.length > 2}
            <div class="digit digit-on"></div>
          {:else}
            <div class="digit"></div>
          {/if}
        </div>

        <div class="digit-container">
          {#if passcode.length > 3}
            <div class="digit digit-on"></div>
          {:else}
            <div class="digit"></div>
          {/if}
        </div>
      </div>

      <div id="element-container">
        <ErrorMessage />
      </div>
      <!-- <div style="height: 10vh;"></div> -->
      <Loading />
    </div><br>

    <div id="spacing"></div>

    <div id="keypad-container">
      <KeyPad length={4} okButton={false} bind:value={passcode} onClick={async () => {
        await loginUpdate($info.phone, passcode)
        passcode = ""
      }}/>
      <!-- <KeyPadOS length={4} okButton={false} bind:value={passcode} onClick={async () => {
        await loginUpdate($info.phone, passcode)
        passcode = ""
      }}/> -->
    </div>

    <!-- <div id="prompt">
      Apăsați pe ecran pentru tastatură
    </div> -->
  </div>
{/if}

<style scoped>
  #page {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    z-index: 9;
    background: var(--offwhite);
  }

  #keypad-container {
    width: var(--container);
    /* height: 100vh; */
    height: 350px;
    margin: auto;
    position: fixed; 
    bottom: 0;
  }

  #element-container {
    width: 100%;
    text-align: center;
    margin-top: 20px;
  }

  #spacing {
    width: 100%;
    height: 100px;
  }

  #container {
    width: 100%;
    height: 30px;
    margin: auto;
    margin-top: 120px;
  }

  #passcode {
    width: 20%;
    height: 100%;
    margin-left: 40%;
    /* position: fixed;
    top: 20vh; */

    display: flex;
    flex-wrap: wrap;
  }

  .digit-container {
    flex: 25%;
    position: relative;
  }

  .digit {
    width: 10px;
    height: 10px;
    border-radius: 100%;
    border: var(--border);

    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
  
  .digit-on {
    background: var(--darkgreen);
  }

  /* #prompt {
    width: 100%;
    position: fixed;
    bottom: 15px;
    color: var(--darkgreen);
    font-family: var(--sans-serif);
    text-align: center;
  } */
</style>