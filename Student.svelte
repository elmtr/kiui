<script>

  export let gradeKey
  export let currentSubject
  export let student

  import {link, location} from "svelte-spa-router"

  console.log(student)
</script>

<!-- <a href="/teacher/{gradeKey}/{$currentSubject}/{student.key}" use:link>{student.lastName} {student.firstName}</a><br> -->
<a href="/teacher/{gradeKey}/{$currentSubject}/{student.key}" use:link >
  <div id="container">
    <div id="name">
      <span>
        {student.lastName} {student.firstName}
      </span>
    </div>

    <div id="info">
      <span>
        Medie: x; Absente: x
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

  #name {
    width: 100%;
    height: 70%;

    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.7em;
    font-weight: 500;
    color: var(--darkgreen);

    position: relative;

  }

  #name span {
    font-family: var(--serif);
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #info {
    width: 100%;

    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.1em;
    color: var(--darkgreen);

    position: relative;
  }

  #info span {
    font-family: var(--sans-serif);
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
</style>