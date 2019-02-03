<template>
  <div id="weather">
    {{ weatherText }}
    <div>
      <img v-bind:src="weatherIcon"/>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      weatherText: '',
      weatherIcon: ''
    }
  },
  methods: {
    showErrorMessage: function () {
      this.weatherText = 'Не вдалось отримати метеорологічні дані :('
    },
    getCurrentWeather: function () {
      this.$http
        .get('http://api.openweathermap.org/data/2.5/weather?q=Lviv,ua&lang=ua&units=metric&APPID=2862e166be4772ddaf6f204c4a291850')
        .then(response => {
          if (response === null && response['status'] !== 200) {
            this.showErrorMessage()
            return
          }

          var temperature = response['body']['main']['temp']
          var humidity = response['body']['main']['humidity']
          var wind = response['body']['wind']['speed']
          var description = response['body']['weather']['0']['description']
          var iconId = response['body']['weather']['0']['icon']

          temperature = temperature > 0 ? '+' + temperature : temperature

          this.weatherText = `${temperature}\u00B0C, ${humidity}%, ${description}, вітер ${wind} м/с`
          this.weatherIcon = `http://openweathermap.org/img/w/${iconId}.png`
        },
        response => {
          this.showErrorMessage()
        })
    }
  },
  created () {
    this.getCurrentWeather()
    setInterval(() => { this.getCurrentWeather() }, 1800000)
  }
}
</script>

<style scoped>
#weather {
  font-size: 2.5em;
  flex-direction: row;
  justify-content: start;
  align-items: center;
}
img {
  margin-left: .5em;
  margin-right: 0;
  margin-top: auto;
  margin-bottom: auto;
  width: 1.2em;
}
</style>
