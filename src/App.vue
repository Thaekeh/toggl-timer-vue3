<template>
<div id="app">
  <TimerBar @save-session="saveSession" @set-error="setError" />
  <div id="error-space">
    <p>{{ error }}</p>
  </div>
  <SavedSessions :savedSessions="savedSessions" />
</div>
</template>

<script>
import TimerBar from './components/TimerBar.vue'
import SavedSessions from './components/SavedSessions.vue'

export default {
  name: 'App',
  components: {
    TimerBar,
    SavedSessions
  },
  data() {
    return {
      savedSessions: [],
      error: ''
    }
  },
  methods: {
    saveSession(item) {
      this.savedSessions.push(item);
    },
    setError(errorMessage) {
      this.error = errorMessage;
    }
  }
}
</script>

<style scoped>
#app {
  width: 80%;
  margin-left: auto;
  margin-right: auto;
}

#error-space {
  height: 30px;
  color: red;
}
</style>
