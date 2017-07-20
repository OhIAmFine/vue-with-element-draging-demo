<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <!-- <h1>{{ msg }}</h1> -->
    <!-- <el-button @click.native="startHacking">Let's do it</el-button> -->
    <!-- <buttonclick></buttonclick> -->
    <!-- <cloumn></cloumn> -->
    <!-- <collapse></collapse> -->
    <!-- <carousel></carousel> -->
    <!-- <card></card> -->
    <sidebar></sidebar>
    <drag></drag>
  </div>
</template>

<script>
import buttonclick from './Buttonclick.vue'
import cloumn from './cloumn.vue'
import collapse from './collapse.vue'
import carousel from './carousel.vue'
import card from './card.vue'
import sidebar from './sidebar.vue'
import drag from './drag.vue'
export default {
  data () {
    return {
      msg: 'Use Vue 2.0 Today!'
    }
  },
  components : {buttonclick,cloumn,collapse,carousel,card,sidebar,drag},
  methods: {
    startHacking () {
      // this.$notify({
      //   title: 'It Works',
      //   message: 'We have laid the groundwork for you. Now it\'s your time to build something epic!',
      //   duration: 6000
      // })
      alert('haha')
    }
  }
}
</script>

<style>
@import url("//unpkg.com/element-ui@1.3.7/lib/theme-default/index.css");
body {

  font-family: Helvetica, sans-serif;
}
</style>
