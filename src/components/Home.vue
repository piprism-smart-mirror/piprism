<template>
  <div>
    <time-component></time-component>
    <date-component></date-component>
  </div>
</template>

<script>
import TimeComponent from './TimeComponent'
import DateComponent from './DateComponent'

export default {
  name: 'HelloWorld',
  components: {
    'time-component': TimeComponent,
    'date-component': DateComponent
  },
  data () {
    return {
    }
  },
  mounted () {
    // sinoptik.ua/informers_js.php?title=4&amp;wind=3&amp;cities=303010783&amp;lang=ua
  }
}
</script>

<style scoped>
</style>
