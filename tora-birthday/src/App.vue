<template>
  <div id="app">
    <div
        class="app__timer"
         v-if="state === STATES.timer"
    >
      <Timer
          :date="BIRTHDAY_DATE"
          @timeElapsed="timeElapsedHandler"
      />
    </div>

    <div
        class="app__activation"
        v-if="state === STATES.activation"
    >
      <Activation
          pass-phrase="I LOVE DANCING"
          @complete="onCompletePassphrase"
      />
    </div>

    <div
        class="app__birthday"
        v-if="state === STATES.birthday"
    >
      <Birthday/>
    </div>
  </div>
</template>

<script>
import Timer from './components/Timer.vue';
import Activation from './components/Activation.vue';
import Birthday from './components/Birthday.vue';

const STATES = {
  timer: 0,
  activation: 1,
  birthday: 2
};

const BIRTHDAY_DATE = (new Date(2021, 4, 2,0, 0)).getTime();

export default {
  name: 'App',
  components: {
    Timer,
    Activation,
    Birthday
  },
  data() {
    return {
      state: STATES.timer,
      STATES,
      BIRTHDAY_DATE
    };
  },
  mounted() {
    if (Date.now() > BIRTHDAY_DATE) {
      this.state = STATES.activation;
    }
  },
  methods: {
    timeElapsedHandler(){
      this.state = STATES.activation;
    },
    onCompletePassphrase(){
      this.state = STATES.birthday;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.app__timer {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
}
</style>
