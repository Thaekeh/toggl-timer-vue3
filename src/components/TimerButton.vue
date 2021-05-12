<template>
  <button id="toggle-timer-button" @click="emitMethod()">
    <CheckCircleIcon />
  </button>
</template>

<script>
import { CheckCircleIcon } from '@heroicons/vue/solid';

export default {
  name: 'TimerButton',
  components: {
      CheckCircleIcon
  },
  methods: {
      emitMethod() {
          this.$emit('on-click')
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
