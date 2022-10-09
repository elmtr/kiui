<script>
  import {link} from 'svelte-spa-router'
</script>

<div id="navbar">
  <a href="/" use:link>home</a>
  <a href="/timetable" use:link>orar</a>
  <a href="/profile" use:link>profil</a>
</div>

<style scoped>
  #navbar {
    width: 100%;
    height: 60px;
    background: var(--gray);
    position: fixed;
    bottom: 0;
  }
</style>