<script>
    import { onMount } from "svelte"


  export let value
  export let length
  export let onClick
  
  // async function addDigit(n) {
  //   if (value.length < length) {
  //     value += n
  //   }

  //   if (value.length === length) {
  //     await onClick()
  //   }
  // }

  // function removeDigit() {
  //   value = value.substr(0, value.length - 1)
  // }

  async function checkLength() {
    console.log("length: " + value.length)
    if (value.length === length) {
      await onClick()
    }
  }

  // onMount(() => {
  //   prompt()
  // })


</script>

<div id="keypad">
  <input placeholder="••••" autocomplete="off" type="password" on:keyup={checkLength} inputmode="numeric" bind:value={value}>
</div>

<style scoped>
  #keypad {
    width: 100%;
    height: 100%;

    background: rgba(0,0,0,0);
    color: rgba(0,0,0,0);
  }

  input {
    margin-top: 40%;
    width: 50%;

    /* border: 1px solid var(--darkgreen); */
    
    border: none;
    background: var(--offwhite);

    border-radius: var(--border-radius);
    outline: none;
    margin-left: 25%;
    
    text-align: center;

    font-family: var(--sans-serif);
    font-size: 3em;
    color: var(--darkgreen);
  }

  input::placeholder {
    color: var(--offwhite);
    -webkit-text-stroke-width: 1px;
    -webkit-text-stroke-color: var(--darkgreen);
    font-weight: 400;
  }
</style>