# vue_with_element_draging_demo
#### vue +Element实现简单的拖拽
###原理
- 第一个通过自定义指令v-drag 绑定元素实现元素的绝对定位拖拽
- 第二个通过元素上绑定@dragstart事件，实现元素的组合拖拽
### 安装
- npm install
- npm run dev
##### 后期待解决事项
- 第一个document.onmouseup 鼠标弹起时不能定位
- 第二个拖拽时元素之间拖拽会合并两个元素，需要优化
