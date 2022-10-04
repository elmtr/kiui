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
    width: 96%;
    height: 80px;

    margin: auto;
    margin-top: 10px;

    background: var(--lightgreen);

    border: 1px solid var(--darkgreen);
    border-radius: 13px;
  }

  #grade {
    width: 100%;
    height: 70%;

    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.7em;
    color: var(--darkgreen);

    position: relative;
  }

  #grade span {
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
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
</style>