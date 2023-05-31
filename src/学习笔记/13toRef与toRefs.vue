<template>
  <div class="app">
    <h2>个人信息</h2>
    {{ person }}
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
import { toRefs,toRef, reactive } from 'vue'
export default {
  /**
   * toRef
   * 作用：创建一个ref对象，其value值指向另一个对象中的某个属性
   * 语法：const name = toRef(person, 'name')
   * 应用：要将响应式对象中的某个属性单独提供给外部使用时
   * 扩展：toRefs与toRef功能一致，但可以批量创建多个ref对象，语法：toRefs(person)
   */
  setup(){
    const person = reactive({
      name: '薛雯婷',
      age: 18,
      job: {
        salary: {
          amway: 1
        }
      }
    })
    const name = toRef(person, 'name')
    return {
      name,
      person,
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
