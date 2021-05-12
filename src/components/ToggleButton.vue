<template>
  <button id="toggle-timer-button" @click="toggleTimer()">
    <PauseIcon v-if="timerIsRunning" id="play-icon" />
    <PlayIcon v-else id="play-icon" />
  </button>
</template>

<script>
import { PlayIcon, PauseIcon } from '@heroicons/vue/solid';

export default {
  name: 'ToggleButton',
  components: {
      PlayIcon,
      PauseIcon
  },
  methods: {
      toggleTimer() {
          this.$emit('toggle-timer')
      }
  },
  props: ['timerIsRunning']
}
</script>

<style scoped>
#toggle-timer-button {
    border: none;
    border-radius: 50%;
    background-color: #9616B6;
    height: 40px;
    width: 40px;
    padding: 0;
}

#toggle-timer-button:hover {
    background-color: #b030d0;
    cursor: pointer;
}
</style>
