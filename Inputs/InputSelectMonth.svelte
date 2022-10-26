<script>

  export let value
  export let list

  import {months} from '../../utils/utils'

</script>

<select id="input" bind:value={value}>
  {#each list as item} 
    <option value={item + 1}>
      {months[item + 1]}
    </option>
  {/each}
</select>

<style scoped>
  #input {
    background: var(--gray);
    width: 100px;
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