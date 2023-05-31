<template>
  <div class="app">
    <h2>数值是： {{ num }}</h2>
    <button @click="num +=1 ">点我 + 1</button>
    <hr>
    <h2>当前点击的鼠标坐标为：X:{{x}} - Y: {{y}}</h2>
  </div>
</template>

<script>
import { ref, toRefs } from 'vue';
import usePoint from '@/hooks/usePoint' // usePoint 是一个定义于hooks内部的方法
export default {
  setup(){
    /**
     * 什么是hook?  - 本质是一个函数，把setup中使用的composition api进行了封装
     * 类似于vue2的mixin
     * 自定义hook的优势： 复用代码，让setup中的逻辑更清楚易懂
     */
    const num = ref(0)
    const point = usePoint()
    return {
      num,
      ...toRefs(point)
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
