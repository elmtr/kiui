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

<div id="container">
  <div id="left" on:click={() => {
    loadSubjects()
    currentSubject.set($prevSubject)
  }}>
    <img src="/img/left-lightgreen.png" alt="">
  </div>

  <span id="name">
    {subjects[gradeKey][$currentSubject].name}
  </span>

  <div id="right" on:click={() => {
    loadSubjects()
    currentSubject.set($nextSubject)
  }}>
    <img src="/img/right-lightgreen.png" alt="">
  </div>
</div>

<style scoped>
  #container {
    width: var(--width);
    height: 60px;
    background: var(--darkgreen);
    border-radius: var(--border-radius);
    margin: auto;
    margin-top: 20px;
    margin-bottom: 20px;

    position: relative;
  }

  #left {
    float: left;
    height: 100%;
    width: 60px;
    position: relative;
  }

  #left img {
    width: 70%;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 5px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #right {
    float: right;
    height: 100%;
    width: 60px;
    position: relative;
  }

  #right img {
    width: 70%;
    margin: 0;
    position: absolute;
    top: 50%;
    right: 5px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #name {
    box-sizing: border-box;
    color: var(--lightgreen);
    font-size: 1.6em;
    font-family: var(--sans-serif);
    font-weight: 600;

    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }
</style>