<script>
  import {link} from 'svelte-spa-router'

  export let location
</script>

<div id="container">
  <div id="navbar">
    <div class="icon-container">
      <a href="/" use:link>
        {#if location === "home"}
          <div class="icon icon-selected">

          </div>
        {:else} 
          <div class="icon icon-not-selected">

          </div>
        {/if}
      </a>
    </div>
    <div class="icon-container">
      <a href="/timetable" use:link>
        {#if location === "timetable"}
          <div class="icon icon-selected">

          </div>
        {:else} 
          <div class="icon icon-not-selected">

          </div>
        {/if}
      </a>
    </div>
    <div class="icon-container">
      <a href="/profile" use:link>
        {#if location === "profile"}
          <div class="icon icon-selected">

          </div>
        {:else} 
          <div class="icon icon-not-selected">

          </div>
        {/if}
      </a>
    </div>
  </div>
</div>

<style scoped>
  #container {
    width: 100%;
    height: 60px;
    background: var(--gray);
    position: fixed;
    bottom: 0;
  }

  #navbar {
    width: 100%;
    height: 100%; 
    display: flex;
    flex-wrap: wrap;
  }

  .icon-container {
    flex: 33%;
    position: relative;
  }

  .icon {
    width: 100%;
    height: 40px;
    background: red;

    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  .icon-selected {
    background: green;
  }

  .icon-not-selected {
    background: purple;
  }




</style>