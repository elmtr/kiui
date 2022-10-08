<script>
  import { onMount } from "svelte"
  import {link} from 'svelte-spa-router'
  import { writable } from "svelte/store"
  import {school, now} from '../stores'

  import {floatToHour} from '../utils/utils'

  export let timetable = {}
  export let day
  export let interval

  let progress = writable(70)

  let roman = ["", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX", "X", "XI", "XII", "XIII"]

  function calcProgress(start, end, number) {
    let reference = ~~end

    let progressVal = 0

    if (number >= reference) {
      let startToRef = 
        Math.round(
          ((reference - 1 + 0.6) - start) * 100
        ) / 100

      let refToTime = (number - reference).toFixed(2)
      progressVal = 
        Number((startToRef + Number(refToTime)).toFixed(2)) * 200
    } else {
      progressVal = (
        (number - start) * 200
      )
    }

    if (progressVal > 100) {
      progressVal = 100
    }
    progress.set(progressVal)

    return ""
  }

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
<a href={`/teacher/${$period.subject.grade.key}`} use:link>
  <div id="container">
    <div id="title">
      <span id="title-content">
        <span id="title-content-filler">Ora curentă:</span> <span id="subject-name">{$period.subject.name}</span>
      </span>
    </div>

    <div id="room">
      <img src="/img/location-lightgreen.png" alt="">
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

    {calcProgress($school.intervals[interval-1].start, $school.intervals[interval-1].end, $now)}
    <div id="progress">
      <div id="progress-bar-container">
        <div id="progress-bar" style={`width: ${$progress}%`}></div>
      </div>
    </div>
  </div>
</a>
{/if}

<style scoped>
  #container {
    width: var(--width);
    height: 120px;

    margin: auto;
    margin-top: 10px;
    padding-top: 15px;

    background: var(--darkgreen);

    border: var(--border);
    border-radius: var(--border-radius);

    position: relative;
  }

  #title {
    color: var(--lightgreen);
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

  #title-content-filler{
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
    color: var(--lightgreen);
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
    color: var(--lightgreen);
    font-size: 1em;
    width: 40%;
  }

  #progress {
    position: absolute;
    bottom: 15px;
    right: 20px;
    font-family: var(--sans-serif);
    color: var(--lightgreen);
    font-size: 1.3em;
    width: 60%;

  }

  #progress-bar-container {
    width: 100%;
    height: 15px;
    background: white;
    border-radius: var(--border-radius);
  }

  #progress-bar {
    height: 15px;
    background: var(--lightgreen);
    border-radius: var(--border-radius);
  }

</style>