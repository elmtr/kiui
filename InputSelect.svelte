<script>

  export let value
  export let list

</script>

<select bind:value={value}>
  {#each list as item} 
    <option value={('0' + (item + 1)).slice(-2)}>
      {('0' + (item + 1)).slice(-2)}
    </option>
  {/each}
</select>