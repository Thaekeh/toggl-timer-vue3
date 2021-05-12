<template>
  <div id="timer-bar">
    <input id="title-input" v-model="sessionTitle" />
    <ToggleButton
      :timerIsRunning="timerIsRunning"
      @toggle-timer="toggleTimer()"
      id="toggle-timer-button"
    />
    <TimerButton @on-click="prepareSave()" />
    <Timer :timeInMilliSeconds="timeInMilliSeconds" :startTime="startTime" />
  </div>
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
      startTime: 0,
      id: 0,
      sessionTitle: "",
      savedSessions: [],
      currentSession: {},
    };
  },
  methods: {
    toggleTimer() {
      this.timerIsRunning = !this.timerIsRunning;
      if (this.timerIsRunning) this.startTimer();
      if (!this.timerIsRunning) this.stopTimer();
    },
    startTimer() {
      this.startTime = Date.now();
      this.interval = setInterval(this.incrementTimer, 10);
    },
    stopTimer() {
      clearInterval(this.interval);
    },
    incrementTimer() {
      this.timeInMilliSeconds += 10;
    },
    prepareSave() {
      if (!this.sessionTitle) {
        this.setError("Please fill in a title");
        return;
      }
      if (!this.startTime) {
        this.setError("Cannot save session when timer hasn't been started yet");
        return;
      }
      this.currentSession = { id: this.getId(), title: this.sessionTitle, startTime: this.startTime };
      this.saveSession();
      this.resetData();
    },
    resetData() {
      this.sessionTitle = '';
      this.setError('');
      this.startTime = 0;
      this.timerIsRunning = false;
    },
    saveSession() {
      this.$emit("save-session", this.currentSession);
    },
    setError(errorMessage) {
      this.$emit("set-error", errorMessage);
    },
    getId() {
      this.id += 1;
      return this.id;
    },
  },
};
</script>

<style scoped>
#timer-bar {
  background-color: #e5e5e5;
  display: flex;
  padding: 5px;
  border-radius: 5px;
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
