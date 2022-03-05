<template>
<EventCalendar />
</template>

<script>
import EventCalendar from './components/EventCalendar.vue'
export default {
  name: 'App',
  components: {
    EventCalendar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #05078f;
  margin-top: 60px;
}
</style>
