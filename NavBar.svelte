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
            <img src="/img/location-darkgreen.png" alt="">
            <span>Acasă</span>
          </div>
        {:else} 
          <div class="icon icon-not-selected">
            <img src="/img/location-lightgreen.png" alt="">
          </div>
        {/if}
      </a>
    </div>
    <div class="icon-container">
      <a href="/timetable" use:link>
        {#if location === "timetable"}
          <div class="icon icon-selected">
            <img src="/img/location-darkgreen.png" alt="">
            <span>Orar</span>
          </div>
        {:else} 
          <div class="icon icon-not-selected">
            <img src="/img/location-lightgreen.png" alt="">
          </div>
        {/if}
      </a>
    </div>
    <div class="icon-container">
      <a href="/profile" use:link>
        {#if location === "profile"}
          <div class="icon icon-selected">
            <img src="/img/location-darkgreen.png" alt="">
            <span>Profil</span>
          </div>
        {:else} 
          <div class="icon icon-not-selected">
            <img src="/img/location-lightgreen.png" alt="">
          </div>
        {/if}
      </a>
    </div>
  </div>
</div>

<style scoped>
  #container {
    /* width: calc(calc(93 * var(--container)) / 100); */
    width: 100%;
    height: 60px;
    background: var(--offwhite);
    box-shadow: 0 1px 5px var(--gray);
    position: fixed;
    /* bottom: 10px; */
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    /* border-radius: var(--border-radius); */
    z-index: 10;
    margin: auto;
  }

  #navbar {
    width: calc(calc(93 * var(--container)) / 100);
    height: 100%; 
    margin: auto;
    display: flex;
    flex-wrap: wrap;
  }

  .icon-container {
    flex: 33%;
    position: relative;
  }

  .icon-selected {
    background: var(--lightgreen);
    width: 95%;
    max-width: 130px;
    height: 70%;
    border-radius: var(--border-radius);
    
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  .icon-selected img {
    height: 80%;

    position: absolute;
    top: 50%;
    left: 10px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  .icon-selected span {
    color: var(--darkgreen);
    font-family: var(--sans-serif);
    position: absolute;
    top: 50%;
    right: 15px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  .icon-not-selected {
    height: 90%;
    width: 100%;
  }

  .icon-not-selected img {
    height: 35px;
    position: absolute;
    top: 50%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  .icon img {
    height: 20px;
  }
</style>