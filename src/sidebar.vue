
<template>
  <div>
    <el-row class="tac">
  <el-col :span="8" v-on:click="clickTest">

    <el-menu  draggable='true' v-drag='dragstart'  :style="style"

     default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" theme="dark" >
      <el-submenu index="1">
        <template slot="title">导航一</template>
        <el-menu-item-group title="分组一">
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <template slot="title">选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">导航二</el-menu-item>
      <el-menu-item index="3">导航三</el-menu-item>
    </el-menu>
  </el-col>
</el-row>
  </div>
</template>

<script>

export default {
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      dragstart(val){
        this.val = val;
      },
      clickTest(){
        alert('clickTest')
      }
    }
  }

</script>
<style >

  .el-menu-vertical-demo{
    font-size:30px;
  }
  .el-menu{
    border-radius: 30px;
  }
</style>