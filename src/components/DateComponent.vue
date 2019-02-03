<template>
  <div id="date">
    {{ date }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      date: '',
      daysOfWeek: [
        'Неділя', 'Понеділок', 'Вівторок', 'Середа', 'Четвер', 'П\'ятниця', 'Субота'
      ]
    }
  },
  created () {
    setInterval(() => {
      var currentDate = new Date()

      var day = currentDate.getDay()
      var date = currentDate.getDate()
      var month = currentDate.getMonth()
      var year = currentDate.getFullYear()

      day = this.daysOfWeek[day]
      date = date > 9 ? date : '0' + date
      month = month > 9 ? month : '0' + month

      this.date = `${day}, ${date}/${month}/${year}`
    }, 1000)
  }
}
</script>

<style scoped>
#date {
  font-size: 3em;
}
</style>
