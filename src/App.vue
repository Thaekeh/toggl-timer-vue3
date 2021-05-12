<template>
<div id="app">
  <TimerBar />
  <SavedSessions />
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
  }
}
</script>
