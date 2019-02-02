<template>
  <div>
    {{ displayDate }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      displayDate: '',
      daysOfWeek: [
        'Понеділок', 'Вівторок', 'Середа', 'Четвер', 'П\'ятниця', 'Субота', 'Неділя'
      ]
    }
  },
  mounted () {
    setInterval(() => {
      var time = new Date()

      var day = time.getDay() - 1
      var date = time.getDate()
      var month = time.getMonth()
      var year = time.getFullYear()

      day = this.daysOfWeek[day]
      date = date > 9 ? date : '0' + date
      month = month > 9 ? month : '0' + month

      this.displayDate = `${day}, ${date}/${month}/${year}`
    }, 1000)
  }
}
</script>

<style scoped>
</style>
