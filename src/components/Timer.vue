<template>
  <div id="timer-container">
    <p id="time-paragraph">
      {{ timeSinceStart() }}
    </p>
  </div>
</template>

<script>
export default {
  name: "Timer",
  props: ["timeInMilliSeconds", "startTime"],
  methods: {
    timeSinceStart() {
      if (this.startTime === 0) return 0;
      const timeInSeconds = Math.floor((Date.now() - this.startTime) / 1000);
      const hours = Math.floor(timeInSeconds / 3600);
      const minutes = Math.floor((timeInSeconds % 3600) / 60);
      const seconds = Math.floor(timeInSeconds % 60);
      return `${this.replaceSingleNumber(hours)}:${this.replaceSingleNumber(
        minutes
      )}:${this.replaceSingleNumber(seconds)}`;
    },
    replaceSingleNumber(number) {
      if (this.isSingleDigit(number)) return `0${number}`;
      return number;
    },
    isSingleDigit(number) {
      return String(+number).charAt(0) == number;
    },
  },
};
</script>

<style scoped>
#time-paragraph {
  display: block;
  margin-bottom: auto;
  margin-top: 10px;
  height: 100%;
}

#timer-container {
  width: 80px;
}
</style>
