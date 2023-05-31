<template>
  <div class="app">
    <input type="text" v-model="keyWord">
    <h2>{{ keyWord }}</h2>
  </div>
</template>

<script>
import { customRef, ref } from 'vue'
export default {
  setup () {
    /** 创建一个自定义的ref,并对具有依赖项跟踪和更新触发进行显示控制 */
    // const keyWord = ref('hello')
    function InkRef (value, delay) {// 自定义ref，实现，输入框输入内容 等1s h2同步展示
      let timer = null
      return customRef((track, trigger) => {
        return {
          get() {
            console.log(`有人从InkRef容器中读取了${value}`);
            track() // 通知vue追踪value的变化（提前和get商量一下，让他认为这个value是有用的）
            return value
          },
          set(newValue) {
            console.log(`有人修改了InkRef容器中的数据, 修改的值为：${newValue}`);
            clearTimeout(timer)
            timer = setTimeout(() => {
              value = newValue
              trigger() // 通知vue去重新解析模板
            }, delay)
          }
        }
      })
    }
    const keyWord = InkRef('hello', 1000) 
    return {
      keyWord
    }
  }
}
</script>
<style lang="scss">
.app {
  background-color: lightpink;
  padding: 10px;
}
</style>
