<template>
  <div id="app">
    <Navigation/>
    <HomePage/>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import HomePage from './components/HomePage.vue'

export default {
  name: 'app',
  components: {
    HomePage,
    Navigation,
  }
}
</script>

<style>
  @import './assets/css/sgc.css';
</style>
