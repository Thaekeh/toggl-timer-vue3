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
  props: ["timeInMilliSeconds", "startDate"],
  methods: {
    timeSinceStart() {
      return Math.floor((Date.now() - this.startDate) / 1000);
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
