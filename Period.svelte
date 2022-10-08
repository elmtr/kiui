<script>
  import {roman, floatToHour} from '../utils/utils'
  import {school} from '../stores'

  export let period
</script>

<div id="container">
  <div id="row" style="font-size: 1.3em;">
    {period.subject.name} - Clasa a {roman[period.subject.grade.gradeNumber]}-a {period.subject.grade.gradeLetter}
  </div>
  <div id="row">
    <div id="interval">
      <span>
        {floatToHour($school.intervals[period.interval].start)} - {floatToHour($school.intervals[period.interval].end)}
      </span>
    </div>
    <div id="room">
      <img src="/img/location-darkgreen.png" alt="">
      <span>
        {period.room}
      </span>
    </div>
  </div>
</div>

<style scoped>
  #container {
    width: var(--width);

    border: var(--border);
    border-radius: var(--border-radius);

    margin: auto;

    box-sizing: border-box;
    padding: 20px 15px 10px 15px;
    margin-bottom: 10px;
  }

  #row {
    height: 30px;
    color: var(--darkgreen);
    font-family: var(--sans-serif);    
    font-weight: 600;
  }

  #interval {
    float: left;
    position: relative;
    height: 100%;
    width: 40%;
    font-size: 1.1em;
    font-weight: 500;
  }

  #interval span {
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

  #room {
    font-size: 1.1em;
    font-weight: 500;
    position: relative;

    width: 40%;
    height: 100%;
    float: right;
  }

  #room span {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 35px;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }
 

  
  #room img {
    height: 85%;
    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
  }

</style>