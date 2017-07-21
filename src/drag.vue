<template>
<div class='drag-content'>
  <div class='project-content'>
    <div class='select-item' draggable='true' @dragstart='drag($event)' v-for='fruit in fruits'>{{fruit.name}}</div>
  </div>
  <div class='people-content'>
    <div class='drag-div' v-for='(preson,presonId) in people' @drop='drop($event)' @dragover='allowDrop($event)'>
      <div class='select-project-item'>
        <label class='drag-people-label'>{{preson.name}}:</label>
      </div>
    </div>
  </div>
</div>
</template>


<script>
let dom = null
export default {
  methods: {//拖拽方法
    drag:function(event){
       dom = event.currentTarget
    },

    drop:function(event){//放置时加入元素
      if(event.target.className !== 'select-item'){
      event.preventDefault();
      event.target.appendChild(dom);
    }
    },

    allowDrop:function(event){//阻止放置时默认事件
      event.preventDefault();
    },
  },

  data() {
    return {
      fruits:[{
        id:1,
        name:'葡萄',
      },{
        id:2,
        name:'芒果',
      },{
        id:3,
        name:'木瓜',
      },{
        id:4,
        name:'榴莲',
      }],
      people:[{
        id:1,
        name:'大雄',
      },{
        id:2,
        name:'胖虎',
      },{
        id:3,
        name:'胖虎爸爸 ',
      },{
        id:3,
        name:'胖虎爷爷',
      }]
    }
  }
}
</script>
<style scoped>
.select-item {
  background-color: #5bc0de;
  display: inline-block;
  text-align: center;
  border-radius: 3px;
  margin-right: 10px;
  cursor:pointer;
  padding: 6px 20px;
  color: #fff;
}
 .cursored{
  cursor: default;
}
.project-content,.people-content {
    margin: 30px 50px;
}
.people-content {
    margin-top: 30px;
}
.drag-div {
    border: 1px solid #5bc0de;
    padding:10px;
    margin-bottom: 10px;
    width: 800px;
    cursor: pointer;
}
.select-project-item {
    display: inline-block;
    text-align: center;
    border-radius: 3px;
}
.drag-people-label{
  margin-bottom:0;
  padding-right:10px;
}
</style>