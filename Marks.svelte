<script>

  export let subjectKey
  export let studentKey

  import {token, marks} from '../stores'
  import {link, location} from 'svelte-spa-router'
  import {fetchMarks} from '../fetch/fetch'

</script>

<h1>marks</h1>
{#await fetchMarks($token, subjectKey, studentKey) then data}
  {#each $marks as mark}
    <span>
      {mark.value} - {mark.dateDay}.{mark.dateMonth}
    </span>
    <br>
  {/each}
  <a href="{$location}/add/mark" use:link> adauga nota</a>
{/await}
