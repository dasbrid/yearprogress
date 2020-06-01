<template>
  <div id="app">
    <YearProgress/>
    <Version version = "1.0" />
  </div>
</template>

<script>
import YearProgress from './components/YearProgress.vue'
import Version from './components/Version.vue'

export default {
  name: 'App',
  components: {
    YearProgress,
    Version
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
