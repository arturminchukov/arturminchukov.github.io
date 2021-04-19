<template>
  <div class="timer">
    <Countdown :deadline="deadline" @timeElapsed="timeElapsedHandler"></Countdown>
  </div>
</template>

<script>
import Countdown from 'vue2-flip-countdown';
import { format } from 'date-fns'

export default {
  name: 'Timer',
  components: {
    Countdown
  },
  props: {
    date: Number
  },
  methods: {
    timeElapsedHandler() {
      this.$emit('timeElapsed');
    }
  },
  computed: {
    deadline() {
      const a = format(new Date(this.date), 'yyyy-MM-dd HH:mm:ss');
      return a;
    }
  }
};
</script>

<style>
.timer {
  background: url("../assets/86bi.gif");
  background-size: contain;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.flip-card {
  font-size: 64px !important;
}

.flip-clock__slot {
  color: #cca900;
  opacity: 0.5;
}
</style>