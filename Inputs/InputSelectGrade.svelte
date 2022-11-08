<script>

  export let value
  export let list

</script>

<select id="input" bind:value={value}>
  {#each list as item} 
    <option value={item}>
      {item}
    </option>
  {/each}
</select>

<style scoped>
  #input {
    background: var(--offwhite);
    width: 80px;
    height: 40px;
    border-radius: var(--border-radius);
    border: var(--border);
    font-size: 17px;
  }

  #input:focus-visible {
    outline: none;
  }

  #input:focus-within {
    outline: none;
  }
</style>