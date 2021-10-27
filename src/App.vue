<template>
  <div id="app">
    <DisplayItem :item="item" />
  </div>
</template>

<script>
import DisplayItem from './components/DisplayItem.vue'

export default {
  name: 'App',
  components: {
    DisplayItem
  },
  data() {
      return {
          item: require('../public/static/node_modules.json')
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
