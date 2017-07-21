<template>
  <div id="app">
    <sidebar-drag></sidebar-drag>
    <drag></drag>
  </div>
</template>

<script>
import sidebarDrag from './sidebar-drag.vue'
import drag from './drag.vue'

export default {
  components : {sidebarDrag,drag}
}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
