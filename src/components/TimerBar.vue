<template>
  <div id="timer-bar">
    <input id="title-input" />
    <ToggleButton
      :timerIsRunning="timerIsRunning"
      @toggle-timer="toggleTimer()"
    />
    <Timer :timeInMilliSeconds="timeInMilliSeconds" :startDate="startDate" />
  </div>
</template>

<script>
import ToggleButton from "./ToggleButton.vue";
import Timer from "./Timer.vue";

export default {
  name: "TimerBar",
  components: {
    ToggleButton,
    Timer,
  },
  data() {
    return {
      timerIsRunning: false,
      timeInMilliSeconds: 0,
      interval: 0,
      startDate: 0
    };
  },
  methods: {
    toggleTimer() {
      this.timerIsRunning = !this.timerIsRunning;
      if (this.timerIsRunning) this.startTimer();
      if (!this.timerIsRunning) this.stopTimer();
    },
    startTimer() {
      this.startDate = Date.now();
      this.interval = setInterval(this.incrementTimer, 10);
    },
    stopTimer() {
      clearInterval(this.interval);
    },
    incrementTimer() {
      this.timeInMilliSeconds += 10;
    }
  },
};
</script>

<style scoped>
#timer-bar {
  background-color: #e5e5e5;
  display: flex;
  margin-left: 10%;
  padding: 5px;
  border-radius: 5px;
  max-width: 75%;
}

#title-input {
  border: 1px solid #e5e5e5;
  border-radius: 5px;
  width: 80%;
  height: 40px;
  font-size: 18px;
  margin-right: 20px;
}
</style>
