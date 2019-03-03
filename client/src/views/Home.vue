<template>
  <div>
    <transition name="slide-fade">
      <time-component v-show="showTime"></time-component>
    </transition>
    <transition name="slide-fade">
      <date-component v-show="showDate"></date-component>
    </transition>
    <transition name="slide-fade">
      <weather-component v-show="showWeather"></weather-component>
    </transition>
    <transition name="slide-fade">
      <news-component v-show="showNews"></news-component>
    </transition>
  </div>
</template>

<script>
// @ is an alias to /src
import TimeComponent from '@/components/TimeComponent'
import DateComponent from '@/components/DateComponent'
import WeatherComponent from '@/components/WeatherComponent'
import NewsComponent from '@/components/NewsComponent'

export default {
  name: 'Home',
  components: {
    'time-component': TimeComponent,
    'date-component': DateComponent,
    'weather-component': WeatherComponent,
    'news-component': NewsComponent
  },
  data () {
    return {
      showTime: false,
      showDate: false,
      showWeather: false,
      showNews: false,
      apiTest: ''
    }
  },
  mounted () {
    setTimeout(() => { this.showTime = true }, 500)
    setTimeout(() => { this.showDate = true }, 1000)
    setTimeout(() => { this.showWeather = true }, 1500)
    setTimeout(() => { this.showNews = true }, 2000)
  }
}
</script>
