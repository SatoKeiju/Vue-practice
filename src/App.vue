<template>
  <div id="app">
    <Timer/>
  </div>
</template>

<script>
import Timer from './components/Timer'

export default {
  name: 'App',
  components: {
    Timer
  }
}
</script>

<style>
#app {
  margin-top: 60px;
}
</style>
