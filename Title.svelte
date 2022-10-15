<script>
  
  export let value

</script>

<div id="title">
  <span>{value}</span>
</div>


<style scoped>
  #title {
    width: 100%;
    height: 50px;
    position: relative;
  }

  #title span {
    color: var(--darkgreen);
    font-family: var(--sans-serif);
    font-size: 1.5em;
    font-weight: 600;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 20px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
</style>