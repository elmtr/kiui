<script>

  export let grade

  import {subjects} from '../stores'
  import {link} from 'svelte-spa-router'

  let roman = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII"]

  function findIndexInArray(item, list) {
    for (let index in list) {
      if (list[index] === item) {
        return Number(index)
      }
    }
  }

</script>

<a href={`/teacher/${grade.key}`} use:link >
  <div id="container">
    <div id="grade">
      <span>
        Clasa a {roman[grade.gradeNumber]}-a {grade.gradeLetter.toUpperCase()}
      </span>
    </div>

    <div id="subjects">
      <span>
        {#if $subjects}
          {#each Object.keys($subjects[grade.key]) as subject} 
            {$subjects[grade.key][subject].name} 
            <!-- {findIndexInArray(subject, Object.keys($subjects[grade.key]))} -->

            {#if findIndexInArray(subject, Object.keys($subjects[grade.key])) + 1 !==  Object.keys($subjects[grade.key]).length }
              -{" "}
            {/if}
          {/each}
        {/if}
      </span>
    </div>
  </div>
</a>

<style scoped>
  #container {
    width: var(--width);
    height: 80px;

    margin: auto;
    margin-top: 10px;

    background: var(--lightgreen);

    border: var(--border);
    border-radius: var(--border-radius);
  }

  #grade {
    width: 100%;
    height: 70%;

    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.7em;
    font-weight: 500;
    color: var(--darkgreen);

    position: relative;

  }

  #grade span {
    font-family: var(--serif);
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #subjects {
    width: 100%;

    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.1em;
    color: var(--darkgreen);

    position: relative;
  }

  #subjects span {
    font-family: var(--sans-serif);
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
</style>