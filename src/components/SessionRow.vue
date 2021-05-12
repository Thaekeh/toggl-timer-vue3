<template>
  <tr>
    <td>
      {{ session.title }}
    </td>
    <td>
      {{ formatDate(session.startTime) }}
    </td>
    <td>
      {{ formatDate(session.endTime) }}
    </td>
    <td>
      {{ formatTimeDifference(session.totalTime) }}
    </td>
  </tr>
</template>

<script>
export default {
  name: "SessionRow",
  props: ["session"],
  methods: {
    formatDate(time) {
      const dateObj = new Date(time);
      const hours = dateObj.getHours();
      const minutes = dateObj.getMinutes();
      const seconds = dateObj.getSeconds();
      return `${this.replaceSingleNumber(hours)}:${this.replaceSingleNumber(minutes)}:${this.replaceSingleNumber(seconds)}`;
    },
    formatTimeDifference(timeInMilliSeconds) {
      const timeInSeconds = timeInMilliSeconds / 1000;
      const hours = Math.floor(timeInSeconds / 3600);
      const minutes = Math.floor((timeInSeconds % 3600) / 60);
      const seconds = Math.floor(timeInSeconds % 60);
      return `${this.replaceSingleNumber(hours)}:${this.replaceSingleNumber(minutes)}:${this.replaceSingleNumber(seconds)}`;
    },
    replaceSingleNumber(number) {
      if (this.isSingleDigit(number)) return `0${number}`;
      return number;
    },
    isSingleDigit(number) {
        return String(+number).charAt(0) == number;
    }
  },
};
</script>
