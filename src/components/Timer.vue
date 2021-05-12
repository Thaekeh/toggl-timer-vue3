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
    margin-top: auto;
    height: 100%;
    /* text-align: center; */
    /* justify-self: center; */
    text-justify: center;
    justify-items: center;
    justify-content: center;
}
</style>
