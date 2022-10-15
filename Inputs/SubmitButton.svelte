<script>

  export let value
  export let onClick

</script>

<input type="submit" {value} on:click={onClick}>

<style scoped>
  input {
    width: 100%;
    height: 50px;
    background: var(--lightgreen);
    color: var(--darkgreen);
    border: none;
    /* border: var(--border); */
    border-radius: var(--border-radius);
    font-size: 1.2em;
  }

  input:focus-visible {
    border: var(--border);
  }
</style>