<script>

  export let value
  export let list

</script>

<select id="input" bind:value={value}>
  {#each list as item} 
    <option value={item + 1}>
      {item + 1}
    </option>
  {/each}
</select>

<style scoped>
  #input {
    background: var(--gray);
    width: 80px;
    height: 40px;
    border-radius: var(--border-radius);
    border: var(--border);
    font-size: 17px;
  }
</style>