<template>
  <div id="timer-bar">
    <input id="title-input" />
    <ToggleButton
      :timerIsRunning="timerIsRunning"
      @toggle-timer="toggleTimer()"
      id="toggle-timer-button"
    />
    <TimerButton @on-click="prepareSave()" />
    <Timer :timeInMilliSeconds="timeInMilliSeconds" :startDate="startDate" />
  </div>
    <li v-for="(item, id) in savedSessions" :key="id">
      {{id}}
    </li>
</template>

<script>
import ToggleButton from "./ToggleButton.vue";
import TimerButton from "./TimerButton.vue";
import Timer from "./Timer.vue";

export default {
  name: "TimerBar",
  components: {
    ToggleButton,
    TimerButton,
    Timer,
  },
  data() {
    return {
      timerIsRunning: false,
      timeInMilliSeconds: 0,
      interval: 0,
      startDate: 0,
      id: 0,
      savedSessions: [],
      currentSession: {}
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
    },
    prepareSave() {
      this.savedSessions.push({id: this.getId()})
    },
    saveSession() {
      this.$emit('save-session', this.currentSession)
    },
    getId() {
      this.id += 1;
      return this.id;
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

#toggle-timer-button {
  margin-right: 10px;
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
