<template>
  <div id="timer">
    <h1>{{this.minutes}} minutes {{this.seconds}} seconds</h1>
    <h1 v-if="Pitch.isEnd">End!</h1>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data () {
    return {
      Pitch: {
        startTime: 0,
        endTime: 3000,
        countSeconds: 0,
        isEnd: false
      }
    }
  },
  computed: {
    minutes: function () {
      return Math.floor(this.Pitch.countSeconds / 60)
    },
    seconds: function () {
      return this.Pitch.countSeconds - this.minutes * 60
    }
  },
  methods: {
    setCountSecond: function () {
      this.Pitch.countSeconds = Math.floor((this.Pitch.endTime - this.Pitch.startTime) / 1000)
    },
    count: function () {
      if (this.seconds === 0) {
        this.complete()
      } else {
        this.countDown()
      }
    },
    start: function () {
      this.timerObject = setInterval(this.count, 1000)
    },
    countDown: function () {
      this.Pitch.countSeconds--
    },
    complete: function () {
      clearInterval(this.timerObject)
      this.Pitch.isEnd = true
    }
  },
  mounted () {
    this.setCountSecond()
    this.start()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #timer {
    text-align: center;
    font-family: 'Overpass', sans-serif;
    font-size: 40px;
  }
</style>
