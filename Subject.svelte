<script>

  export let subject

  import {link} from 'svelte-spa-router'

</script>

<a href={`/student/${subject.key}`} use:link >
  <div id="container">
    <div id="subject">
      <span>
        {subject.name}
      </span>
    </div>

    <div id="subjects">
      
    </div>
  </div>
</a>

<style scoped>
  #container {
    width: var(--width);

    box-sizing: border-box;
    padding: 10px 0;

    margin: auto;
    margin-top: 10px;

    background: var(--lightgreen);

    border: var(--border);
    border-radius: var(--border-radius);
  }

  #subject {
    width: 100%;
    height: 40px;


    box-sizing: border-box;
    padding-left: 20px;

    font-size: 1.7em;
    font-weight: 500;
    color: var(--darkgreen);

    position: relative;

  }

  #subject span {
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
</style>