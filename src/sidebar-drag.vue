
<template>
  <div>
    <el-row class="tac">
  <el-col :span="8" >
    <el-menu  draggable='true' v-drag='dragstart' 
     default-active="2" class="el-menu-vertical-demo" theme="dark" >
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
import Vue from 'vue'

Vue.directive('drag',//自定义指令                                      JS
        {bind:function (el, binding) {
                let oDiv = el;   //当前元素
                let self = this;  //上下文
                oDiv.onmousedown = function (e) {
                 //鼠标按下，计算当前元素距离可视区的距离
                    let disX = e.clientX - oDiv.offsetLeft;
                    let disY = e.clientY - oDiv.offsetTop;

                    document.onmousemove = function (e) {
                        e.preventDefault();
                      //通过事件委托，计算移动的距离 
                        let l = e.clientX - disX;
                        let t = e.clientY - disY;
                      //移动当前元素  
                        oDiv.style.left = l + 'px';
                        oDiv.style.top = t + 'px';
                        console.log('left:'+l+'top:'+t)
                    };
                    document.onmouseup = function (e) {
                      console.log('mouseup');
                        document.onmousemove = null;
                        document.onmouseup = null;
                     };
                };
            }
        }
    );

export default {
  methods : {
    dragstart : function (){
      console.log('start draging');
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