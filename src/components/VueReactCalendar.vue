<template>
  <div>
    <p>Here comes the Web Component</p>
    <event-calendar :mode="mode" :first="first"/>
  </div>
</template>

<script>
export default {
  name: 'VueCalendar',
  props:{

}}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
