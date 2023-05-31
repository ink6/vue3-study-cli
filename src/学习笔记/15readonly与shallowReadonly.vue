<template>
  <div class="app">
    <h2>个人信息</h2>
    <h2>姓名：{{ name }} </h2>
    <button @click="name += '~'">修改姓名</button> 
    <hr>
    <h2>年龄：{{ age }} </h2>
    <button @click="age ++">增加年龄</button> 
    <hr>
    <h2>薪资：{{ job.salary.amway }} K</h2>
    <button @click="job.salary.amway  ++">涨薪</button>
  </div> 
</template>

<script>
import { toRefs, reactive, readonly, shallowReadonly} from 'vue'
export default {
  setup(){
    /**
     * readonly 与shallowReadonly
     * readonly 让一个响应式数据变为只读的（深只读）
     * shallowReadonly 让一个响应式数据变为只读的（浅只读）
     * 应用场景： 不希望数据被修改时
     */
    let person = reactive({
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    person = readonly(person) // 所有的数据都不能修改
    person = shallowReadonly(person) // 浅层次的数据不能修改 深层次的数据可以修改
    console.log(person);
    return {
      ...toRefs(person)
    }
  }
}
</script>
<style lang="scss">
.app {
  padding: 10px;
}
</style>
