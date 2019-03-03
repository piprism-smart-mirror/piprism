<template>
  <div id="news">
    <a href="https://newsapi.org/">powered by NewsAPI.org</a>
    <transition-group name="list">
      <div v-for="article in news" :key="article.title" class="list-item article">
        <div>
          <img v-bind:src="article.image"/>
        </div>
        <div>
          <h4 class="article-title">{{ article.title }}</h4>
          <div class="article-time">{{ article.time }}</div>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  data () {
    return {
      news: []
    }
  },
  methods: {
    addArticle: function (article, delay) {
      setTimeout(() => { this.news.push(article) }, delay)
    },
    showErrorMessage: function () {
      this.addArticle({
        title: 'Не вдалось отримати останні новини :('
      }, 0)
    },
    formatTime: function (time) {
      var date = time.getDate()
      var month = time.getMonth()
      var year = time.getFullYear()
      var hours = time.getHours()
      var minutes = time.getMinutes()

      date = date > 9 ? date : '0' + date
      month = month > 9 ? month : '0' + month
      hours = hours > 9 ? hours : '0' + hours
      minutes = minutes > 9 ? minutes : '0' + minutes

      return `${date}/${month}/${year}, ${hours}:${minutes}`
    },
    getLatestNews: function () {
      var url = 'https://newsapi.org/v2/top-headlines?'
      var country = 'ua'
      var authHeader = { 'X-Api-Key': '656971cf7fe74823aa24fc9853aa1c99' }
      this.$http.get(`${url}country=${country}`, { headers: authHeader }).then(response => {
        if (response === null || response['status'] !== 200) {
          this.showErrorMessage()
          return
        }

        var i = 0
        this.news = []
        for (var article of response['body']['articles']) {
          this.addArticle({
            title: article.title,
            image: article.urlToImage,
            time: this.formatTime(new Date(article.publishedAt))
          }, i)
          i += 300
        }
      },
      response => {
        this.showErrorMessage()
      })
    }
  },
  mounted () {
    setTimeout(() => { this.getLatestNews() }, 2000)
    setInterval(() => { this.getLatestNews() }, 1800000)
  }
}
</script>

<style scoped>
a {
  color: white;
  text-decoration: none;
  font-weight: normal;
  font-size: .7em;
  margin-top: 1em;
  align-self: flex-end;
}
img {
  margin-left: 0;
  margin-right: 1em;
  margin-top: auto;
  margin-bottom: auto;
  width: 6em;
}
.article {
  flex-direction: row;
  align-items: flex-start;
  padding-top: 1em;
}
.article-title {
  margin: 0;
  margin-bottom: 0.2em;
  font-size: 1.1em;
  text-align: justify;
}
.article-time {
  font-weight: normal;
  font-size: .8em;
}
</style>
