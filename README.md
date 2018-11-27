# vue-imgs-view

## 安装
```
npm install vue-imgs-view
```
### 介绍
基于img-vuer，添加了除指令方式绑定事件外，通过父级容器去为内部所有图片添加点击放大查看功能。
添加该方法，主要用于为富文本内容中的图片的全屏浏览，原插件只提供了指令方式，不便用于动态生成的dom。


### 使用

main.js
```
import Gallery from 'vue-imgs-view'
Vue.use(Gallery, {
    swipeThreshold: 100
})

```

```
<div id="wrap">
  <img src="#">
  <img src="#">
</div>
```
*.vue
```
//第一个参数传入容器dom， 第二个为轮播图的组名，根据组名区分轮播组
this.$initGallery(document.getElementById('wrap'), 'groupName')

//离开的时候需要清除当前组
beforeDestroy() {
    this.$removeGallery('groupName');
  },
```

也可以通过全局组件，异步内容需要通过v-if控制组件渲染
```
<Gallery v-if="show" :group="groupName">
        <div style="overflow:hidden" >
          <img class="thumbnail" v-for="img in list1" :src="img.src" :key="img.src">
        </div>
</Gallery>
```