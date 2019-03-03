<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style>
/* common look and feel for whole app */
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-family: 'Montserrat', sans-serif;
  font-weight: bold;
  color: white;
  background-color: black;
  margin: 0;
  padding: 0;
}
div {
  display: flex;
  flex-direction: column;
}
/* animations */
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
