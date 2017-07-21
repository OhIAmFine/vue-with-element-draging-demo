# vue_with_element_draging_demo
#### vue +Element实现简单的拖拽

### 安装
- cnpm install(淘宝镜像安装)
- webpack -d
- npm run dev(监听本地8080端口)

### 原理
- 第一个sidebar-drag.vue通过自定义指令v-drag 绑定元素,实现元素的绝对定位拖拽

``` 
import Vue from 'vue'
Vue.directive('drag',//自定义指令                                      
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
  ```
- 第二个drag.vue通过元素上绑定@dragstart事件,阻止默认事件，元素放置时的判断，实现元素的组合拖拽
 ```
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
    }

<div class='select-item' draggable='true' @dragstart='drag($event)' v-for='fruit in fruits'>{{fruit.name}}</div>

<div class='drag-div' v-for='(preson,presonId) in people' @drop='drop($event)' @dragover='allowDrop($event)'>

```

### 两个拖拽比较异同
- sidebar-drag.vue优点：中拖拽的元素为绝对定位，事先要设置父元素的position,灵活性较好，兼容性较好
- sidebar-drag.vue缺点：只关心拖拽本元素，和其他元素之间没有关联，如果要设置和其他元素的交互比较麻烦，如显示到拖拽到另一个元素内的日志
- drag.vue优点：drag.vue中使用的时html的拖拽事件，容易实现与其他元素的交互，不为绝对定位，管理状态比较容易
- drag.vue缺点：只能在设置了dragover的元素上实现拖拽，规范了实现空间，只在IE和移动端部分支持

##### 后期待解决事项 => 已解决
- 第一个document.onmouseup 鼠标弹起时不能定位
- 第二个拖拽时元素之间拖拽会合并两个元素，需要优化


