## NextTick 是什么呢？

这就要从一个现象来谈起了

![](https://pic.imgdb.cn/item/660925839f345e8d03be60cf.png)

```html
<template>
  <div class="app">
    <h2 class="title">当前计数：{{ counter }}</h2>
    <button @click="increment">+1</button>
    <el-config-provider :locale="zhCn">
      <router-view></router-view>
    </el-config-provider>
  </div>
</template>

<script setup lang="ts">
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'
import { ref } from 'vue'
const counter = ref(100)
function increment() {
  counter.value++

  // DOM 操作
  const titleEl = document.querySelector('.title')
  console.log(titleEl?.textContent)
}
</script>

<style scoped>
.app {
  width: 100vw;
  height: 100vh;
}
</style>
```

上面就演示了当用户点击按钮后，但是控制台的打印却还是上一次的值，此时控制台拿到的是页面改变之前的值，这也反映出，coUnter 没有最新到最新的 Dom 上面去，在开发里面就很有可能会有这个现象，尤其是在你完成了一个操作之后又依赖于上一个操作的值去完成下一个操作的时候。

vue.js 提供了一个 nextTick 函数来解决这一个问题

```html
<template>
  <div class="app">
    <h2 class="title">当前计数：{{ counter }}</h2>
    <button @click="increment">+1</button>
    <el-config-provider :locale="zhCn">
      <router-view></router-view>
    </el-config-provider>
  </div>
</template>

<script setup lang="ts">
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'
import { ref } from 'vue'
const counter = ref(100)
function increment() {
  counter.value++

  // DOM 操作
  nextTick(() => {
    const titleEl = document.querySelector('.title')
    console.log()
  })
}
</script>

<style scoped>
.app {
  width: 100vw;
  height: 100vh;
}
</style>
```

来看到官方解释：

nextTick 等待下一次 DOM 更新刷新的工具方法。

类型

```ts
function nextTick(callback?: () => void): Promise<void>
```

详细信息

当你在 Vue 中更改响应式状态时，**最终的 DOM 更新并不是同步生效的**，而是由 Vue 将它们**缓存在一个队列中**，直到下一个“tick”才一起执行。**这样是为了确保每个组件无论发生多少状态改变，都仅执行一次更新。**

nextTick() 可以在状态改变后立即使用，以等待 DOM 更新完成。你可以传递一个回调函数作为参数，或者 await 返回的 Promise。

其实只要记住，nextTick可以保证 DOM 已经更新完了，然后再去执行里面的回调

