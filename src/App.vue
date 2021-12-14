<template>
  <div id="app">
    <GoogleAuth/>
  </div>
</template>

<script>
import GoogleAuth from './components/GoogleAuth.vue'

export default {
  name: 'App',
  components: {
    GoogleAuth
  }
}
</script>

<style>
#app {
  text-align: center;
}
</style>
