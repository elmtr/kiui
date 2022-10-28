<script>

  export let value
  export let onClick

</script>

<input type="submit" {value} on:click={onClick}>

<style scoped>
  input {
    width: 100%;
    height: 45px;
    background: var(--darkgreen);
    color: var(--lightgreen);
    border: none;
    border: var(--border);
    border-radius: var(--border-radius);
    font-size: 1em;
  }

  input:focus-visible {
    border: var(--border);
  }
</style>