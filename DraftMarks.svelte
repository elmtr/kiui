<script>

  export let subjectKey
  export let studentKey

  import {token, draftMarks} from '../stores'
  import {link, location} from 'svelte-spa-router'
  import {fetchDraftMarks} from '../fetch/fetch'

</script>

<h1>draft marks</h1>
{#await fetchDraftMarks($token, subjectKey, studentKey) then data}
  {#each $draftMarks as draftMark}
    <a href="{$location}/modify/{draftMark.key}" use:link>
      {draftMark.value} - {draftMark.dateDay}.{draftMark.dateMonth}
    </a> -- 
    <a href="{$location}/definitivate/{draftMark.key}" use:link>
      definitiveaza
    </a>
    <br>
  {/each}
  <a href="{$location}/add/draftmark" use:link> adauga nota</a>
{/await}
