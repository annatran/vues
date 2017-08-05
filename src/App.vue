<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> <br /> -->
    <!-- <hello></hello> -->
    <countdown date="May 27, 2018"></countdown>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Countdown from './components/Countdown';

export default {
  name: 'app',
  components: {
    Hello, Countdown
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
