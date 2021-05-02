<template>
  <div class="calendar">
    <Calendar />
  </div>
</template>

<script>
import Calendar from "./components/Calendar";
export default {
  name: "App",
  components: {
    Calendar,
  },
};
</script>

<style lang="sass">
@import "~bulma"

.calendar
  position: relative
  height: 90vh !important
</style>
