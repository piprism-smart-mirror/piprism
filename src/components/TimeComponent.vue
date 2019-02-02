<template>
  <div>
    {{ displayTime }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      displayTime: ''
    }
  },
  mounted () {
    setInterval(() => {
      var time = new Date()

      var hours = time.getHours()
      var minutes = time.getMinutes()
      var seconds = time.getSeconds()

      hours = hours > 9 ? hours : '0' + hours
      minutes = minutes > 9 ? minutes : '0' + minutes
      seconds = seconds > 9 ? seconds : '0' + seconds

      this.displayTime = hours + ':' + minutes + ':' + seconds
    }, 500)
  }
}
</script>

<style scoped>
</style>
