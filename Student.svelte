<script>

  export let gradeKey
  export let currentSubject
  export let student

  import {link} from "svelte-spa-router"

</script>

<a href="/teacher/{gradeKey}/{$currentSubject}/{student.key}" use:link>{student.lastName} {student.firstName}</a><br>
