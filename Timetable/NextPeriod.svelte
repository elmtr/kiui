<script>
  import {link} from 'svelte-spa-router'
  import { writable } from "svelte/store"
  import {school, today, interval, timetable} from '../../stores'

  import {floatToHour} from '../../utils/utils'

  export let user

  let roman = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII"]


  let period = writable($timetable[$today][$interval + 1][0])
  $: {
    period.set($timetable[$today][$interval + 1][0])
  }

  let linkTo = ""
  $: {
    if ($period) {
      if (user === 'student') {
        if ($period.subject.key === "0") {
          linkTo = "/"
        } else {
          linkTo = '/' + user + '/' + $period.subject.key
        }
      } else if (user === 'teacher') {
        linkTo = '/' + user + '/' + $period.subject.grade.key
      }
    }
  }
</script>

{#if $period}
  <a href={linkTo} use:link>
    <div id="container">
      <div id="title">
        <span id="title-content">
          <span id="title-content-filler">Ora următoare:</span> 
          <br><span id="subject-name">{$period.subject.name}</span>
        </span>
      </div>

      <div id="room">
        <img src="/img/location.svg" alt="">
        <span>
          {$period.room}
        </span>
      </div>

      <div id="grade">
        {#if user === "teacher"}
          <span id="grade-grade">
            Clasa  
            <span style="font-weight: 600">{roman[$period.subject.grade.gradeNumber]}{$period.subject.grade.gradeLetter.toUpperCase()}</span>
          </span>
        {/if}
        <br>

        <span id="grade-interval">
          {floatToHour($school.intervals[$interval + 1].start)}-
          {floatToHour($school.intervals[$interval + 1].end)}
        </span>
      </div>
    </div>
  </a>
{/if}

<style scoped>
  #container {
    width: var(--width);
    height: 120px;

    margin: auto;
    margin-bottom: 15px;
    padding-top: 10px;

    background: var(--white);

    border: var(--border);
    border-radius: var(--border-radius);

    position: relative;
  }

  #title {
    color: var(--black);
    height: 40%;
    position: relative;
    font-weight: 600;
  }

  #title-content {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 20px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);  
    font-size: 1.25em;
  }

  #title-content-filler {
    font-family: var(--sans-serif);
  }

  #subject-name {
    font-family: var(--serif);
  }

  #room {
    width: 100%;
    height: 20%;
    position: relative;
    font-size: 1em;
    color: var(--black);
    font-family: var(--sans-serif);
  }

  #room span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 40px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #room img {
    height: 85%;
    margin: 0;
    position: absolute;
    top: 50%;
    left: 15px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #grade {
    position: absolute;
    bottom: 15px;
    left: 20px;
    font-family: var(--sans-serif);
    color: var(--black);
    font-size: 1em;
    width: 40%;
  }

</style>