<script>
  import {link} from 'svelte-spa-router'
  import { writable } from "svelte/store"
  import {school, today, interval, now, timetable,} from '../../stores'

  import {floatToHour} from '../../utils/utils'

  export let user = "teacher"

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

  let period = writable($timetable[$today][$interval][0])
  $: {
    period.set($timetable[$today][$interval][0])
  }

  console.log($school.intervals[$interval])

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
        <span id="title-content-filler">Ora curentă:</span> 
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
        {floatToHour($school.intervals[$interval].start)}-
        {floatToHour($school.intervals[$interval].end)}
      </span>
    </div>

    {calcProgress($school.intervals[$interval].start, $school.intervals[$interval].end, $now)}
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
    height: 130px;

    margin: auto;
    margin-top: 10px;
    padding-top: 12px;

    background: var(--darkgreen);

    border: var(--border);
    border-radius: var(--border-radius);

    position: relative;
  }

  #title {
    color: var(--lightgreen);
    height: 35%;
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
    margin-bottom: 10px;

  }

  #title-content-filler{
    font-family: var(--sans-serif);
  }

  #subject-name {
    font-family: var(--serif);
    margin-top: 10px;
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
    height: 70%;
    filter: var(--lightgreen-filter);
    margin: 0;
    position: absolute;
    top: 50%;
    left: 15px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #grade {
    position: absolute;
    bottom: 20px;
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