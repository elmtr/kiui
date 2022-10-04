<script>

  export let subjects
  export let gradeKey
  export let currentSubject

  import {writable} from 'svelte/store'

  const nextSubject = writable("");
  // const currentSubject = writable("")
  currentSubject.set(Object.keys(subjects[gradeKey])[0])
  const prevSubject = writable("");
  
  let subjectKeys = Object.keys(subjects[gradeKey]).concat(Object.keys(subjects[gradeKey]))

  function loadSubjects() {
    for (let i = 0; i <= subjectKeys.length - 1; i++) {
      if (subjectKeys[i] == $currentSubject) {
        nextSubject.set(subjectKeys[i + 1])
        break 
      }
    }

    for (let i = subjectKeys.length - 1; i >= 1; i--) {
      if (subjectKeys[i] == $currentSubject) {
        prevSubject.set(subjectKeys[i - 1])
        break
      }
    }
  }

</script>

<span on:click={() => {
  loadSubjects()
  currentSubject.set($prevSubject)
}}>prev</span>

<div>
  {subjects[gradeKey][$currentSubject].name}
</div>

<span on:click={() => {
  loadSubjects()
  currentSubject.set($nextSubject)
}}>next</span><br>