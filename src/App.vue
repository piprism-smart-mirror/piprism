<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  font-weight: bold;
  color: white;
  background-color: black;
  margin: 0;
  padding: 0;
}
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .3s ease;
}
.slide-fade-enter, .slide-fade-leave-to {
  transform: translateX(-200px);
  opacity: 0;
}
.list-enter-active, .list-leave-active {
  transition: all .3s ease;
}
.list-enter, .list-leave-to {
  transform: translateX(-200px);
  opacity: 0;
}
</style>
