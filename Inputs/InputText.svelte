<script>

  export let value
  export let label
  export let placeholder
  export let preinput

</script>

<div id="container">
  <div id="label">{label}</div>
  <div id="input">
    {#if preinput !== ""}
      <div id="pre-input">
        <span>{preinput}</span>
      </div>
      <input type="text" placeholder={placeholder} bind:value={value}>
    {:else}
      <input type="text" placeholder={placeholder} bind:value={value} style="left: 10px;">
    {/if}
  </div>
</div>

<style scoped>
  #container {
    width: var(--width);

    margin: auto;
    background: var(--white);
    border-radius: var(--border-radius);

    box-sizing: border-box;
    padding: 20px 10px 15px 10px;
    margin-bottom: 10px;
  }

  #label {
    background: var(--white);
    width: 100%;
    height: 30%;
    
    font-family: var(--sans-serif);
    font-size: 1em;
    color: var(--darkgreen);
    font-weight: 600;
    
    box-sizing: border-box;
    padding-left: 10px;
  }

  #input {
    width: 100%;
    height: 40px;
    background: var(--white);

    position: relative;
  }

  #pre-input {
    float: left;
    height: 100%;
    width: 30px;
    margin-left: 5px;
    background: var(--white);
    position: relative;
    font-family: var(--sans-serif);
    color: var(--darkgreen);
    font-weight: 600;
  }

  #pre-input span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  input {
    background: var(--white);
    color: var(--darkgreen);
    height: 25px;
    width: 250px;
    border: none;
    padding: none;
    font-size: 15px;

    margin: 0;
    position: absolute;
    top: 50%;
    left: 45px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  input:focus-visible {
    outline: none;
  }

  input:focus-within {
    outline: none;
  }
</style>

