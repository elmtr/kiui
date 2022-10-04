<script>
  export let timetable = {}
  export let day
  export let interval
</script>

{#if timetable[day][interval][0]}
  {timetable[day][interval][0].subject.grade.gradeNumber}{timetable[day][interval][0].subject.grade.gradeLetter} - {timetable[day][interval][0].subject.name}
  {day} - {interval}
{/if}