<template>
  <div>
    <table id="session-table">
      <tr>
        <th>Title</th>
        <th>Start Time</th>
        <th>End Time</th>
        <th>Total Time</th>
      </tr>
      <SessionRow
        v-for="(session, id) in savedSessions"
        :key="id"
        :session="session"
      />
    </table>
  </div>
</template>

<script>
import SessionRow from "./SessionRow.vue";

export default {
  name: "SavedSessions",
  props: ["savedSessions"],
  components: {
    SessionRow,
  },
};
</script>

<style scoped>
* {
  color: #fff;
}

#session-table {
  width: 100%;
}
</style>
