<template>
  <div id="app">
    <TitleBar title="Mini Browser" :ico="require('./assets/vue-logo.png')"/>
    <div>
      <router-view></router-view>
    </div>
  </div>
</template>
<script>
  import TitleBar from './components/TitleBar'

  export default {
    name: "App",
    components: {
      TitleBar
    }
  }
</script>
<style>
  #app {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  }
</style>