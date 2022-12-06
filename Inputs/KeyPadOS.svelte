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

<input type="text" on:keyup={checkLength} inputmode="numeric" bind:value={value}>

<style scoped>
  input {
    width: 100%;
    height: 100%;
    /* background: var(--offwhite);
    color: var(--offwhite); */

    background: rgba(0,0,0,0);
    color: rgba(0,0,0,0);
    border: none;
    outline: none;
  }
</style>