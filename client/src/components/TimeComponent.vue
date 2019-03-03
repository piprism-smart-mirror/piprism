<template>
  <div id="time">
    {{ time }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      time: ''
    }
  },
  created () {
    setInterval(() => {
      var currentTime = new Date()

      var hours = currentTime.getHours()
      var minutes = currentTime.getMinutes()
      var seconds = currentTime.getSeconds()

      hours = hours > 9 ? hours : '0' + hours
      minutes = minutes > 9 ? minutes : '0' + minutes
      seconds = seconds > 9 ? seconds : '0' + seconds

      this.time = hours + ':' + minutes + ':' + seconds
    }, 500)
  }
}
</script>

<style scoped>
#time {
  font-size: 4em;
}
</style>
