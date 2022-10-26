<script>
  import {link} from 'svelte-spa-router'
  import { writable } from "svelte/store"
  import {school} from '../../stores'

  import {floatToHour} from '../../utils/utils'

  export let timetable = {}
  export let day
  export let interval
  export let user

  let roman = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII"]

  function findHourInterval(intervals, number) {
    for (let intervalIndex in intervals) {
      let interval = intervals[intervalIndex]
      if (interval.number === number) {
        return interval
      }
    }
  }

  let period = writable(timetable[day][interval][0])
</script>

{#if $period}
  <a href={`/${user}/${$period.subject.grade.key}`} use:link>
    <div id="container">
      <div id="title">
        <span id="title-content">
          <span id="title-content-filler">Ora următoare:</span> <span id="subject-name">{$period.subject.name}</span>
        </span>
      </div>

      <div id="room">
        <img src="/img/location.png" alt="">
        <span>
          {$period.room}
        </span>
      </div>

      <div id="grade">
        <span id="grade-grade">
          Clasa  
          <span style="font-weight: 600">{roman[$period.subject.grade.gradeNumber]}{$period.subject.grade.gradeLetter.toUpperCase()}</span>
        </span>
        <br>

        <span id="grade-interval">
          {floatToHour(findHourInterval($school.intervals, interval).start)}-
          {floatToHour(findHourInterval($school.intervals, interval).end)}
        </span>
      </div>
    </div>
  </a>
{/if}

<style scoped>
  #container {
    width: var(--width);
    height: 90px;

    margin: auto;
    padding-top: 15px;

    background: var(--white);

    border: var(--border);
    border-radius: var(--border-radius);

    position: relative;
  }

  #title {
    color: var(--black);
    height: 20%;
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