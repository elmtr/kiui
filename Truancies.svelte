<script>

  export let subjectKey
  export let studentKey

  import {token, truancies} from '../stores'
  import {link, location} from 'svelte-spa-router'
  import {fetchTruancies} from '../fetch/fetch'

</script>

<h1>truancies</h1>
{#await fetchTruancies($token, subjectKey, studentKey) then data}
  {#each $truancies as truancy}
    <span>
      {truancy.dateDay}.{truancy.dateMonth} - 
      {#if truancy.motivated} 
        motivata
      {:else}
        <a href="{$location}/motivate/{truancy.key}" use:link>nemotivata</a>
      {/if}
    </span>
    <br>
  {/each}
  <a href="{$location}/add/truancy" use:link> adauga absenta</a>
{/await}