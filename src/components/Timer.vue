<template>
  <div>
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
      return Math.floor((Date.now() - this.startTime) / 1000);
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
</style>
